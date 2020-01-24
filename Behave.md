# Behave

## Feature
Written by your Business Analyst / Sponsor in Gherkin language in files with name as `xxx.feature`. They are written in natural language.
Features are composed of scenarios. 
They can have a description, a background and a set of tags.
```gherkin
@tags  @tag
Feature: feature name
 description
 further description

  Background: some requirement of this test
      Given some setup condition
      And some other setup action

  Scenario: some scenario
      Given some condition
      When some action is taken
      Then some result is expected.
  ```

## Background
Is a series of steps similar to scenarios - allows to add some context to the scenarios of a feature.
Background is executed before each scenario of the feature.
Useful for setup basic state:
-   logging into a web browser 
-   setting up a database with test data used by the scenarios.

## Scenarios
Scenarios describe the discrete behaviors being tested.
Scenarios are composed of a series of steps. Steps typically take the form of `Given`, `When`, `Then`.
Scenario should test only one behavior or desired outcome.

## Scenario Outlines
Used when you have a set of expected conditions and outcomes to go along with your scenario steps.
_behave_ will run the scenario once for each (non-heading) line appearing in the example data tables.
```gherkin
Scenario Outline: Blenders
    Given I put <thing> in a blender,
    When I switch the blender on
    Then it should transform into <other thing>

Examples: Amphibians
  | thing         | other thing |
  | Red Tree Frog |        mush |

Examples: Consumer Electronics
  | thing        | other thing |
  | iPhone       | toxic waste |
  | Galaxy Nexus | toxic waste |
```

## Steps
Steps start with _keyword_: of `Given`,  `When`,  `Then`,  `And`, `But`.
Steps are implemented using Python code in directory `steps/xxxx.py`. _All_ modules in the “steps” directory are imported by _behave_ at startup to discover the step implementations. 
_behave_ doesn’t technically distinguish between the various kinds of steps - but you should.

- **Given** - put the system in a known state = _setup_ 
(before user starts interacting with the system)

- **When** - interact with the system (key actions) = _test case step_
(causes some changes to system state)

- **Then** - observe outcomes - _output_

- **And, But**
```gherkin
Scenario: Multiple Givens
    Given one thing
    And another thing
    And yet another thing
    When I open my eyes
    Then I see something
    But I don't see something else
```

### Step Data
You can assign data to the step. This can be useful for loading specific required data into a model.
The table is available to the Python step code as the `.table` attribute in the `Context` variable passed into each step function.
The table is an instance of `Table`.
```gherkin
Scenario: some scenario
 Given a set of specific users
    | name      | department  |
    | Barry     | Beer Cans   |
    | Pudey     | Silly Walks |
    | Two-Lumps | Silly Walks |

     When we count the number of people in each department
     Then we will find two people in "Silly Walks"
     But we will find one person in "Beer Cans"
```

## Tags
Tags may be used to control your test run. You may tag features, scenarios or scenario outlines but nothing else.
Any tag in a feature will be inherited by its scenarios and scenario outlines.
```gherkin
@wip  @slow
Feature: annual reporting
 Some description of a slow reporting system.
```

### Controlling Your Test Run With Tags
```gherkin
Feature: Fight or flight
 In order to increase the ninja survival rate,
 As a ninja commander
 I want my ninjas to decide whether to take on an
 opponent based on their skill levels

@slow
Scenario: Weaker opponent
    Given the ninja has a third level black-belt
    When attacked by a samurai
    Then the ninja should engage the opponent

Scenario: Stronger opponent
    Given the ninja has a third level black-belt
    When attacked by Chuck Norris
    Then the ninja should run for his life
```
Running `behave --tags=slow` will run _just_ the scenarios tagged `@slow`.
Running `behave --tags="not slow` will run everything _except_ the `@slow`.

###  Accessing Tag Information In Python
There are also environmental controls specific to tags, so in the above example _behave_ will attempt to invoke an `environment.py` function `before_tag` and `after_tag` before and after the Scenario tagged `@slow`, passing in the name “slow”. If multiple tags are present then the functions will be called multiple times with each tag in the order they’re defined in the feature file.

Re-visiting the example from above; if only some of the features required a browser and web server then you could tag them `@fixture.browser` and `@fixture.webserver`:
```gherkin
# -- FILE: features/environment.py
from behave.fixture import fixture, use_fixture_by_tag

@fixture
def webserver(context):
    # -- STEP: Setup browser fixture
    context.server = simple_server.WSGIServer(("", 8000))
    context.server.set_app(web_app.main(environment='test'))
    context.thread = threading.Thread(target=context.server.serve_forever)
    context.thread.start()
    yield context.server
    # -- STEP: Teardown/cleanup fixture
    context.server.shutdown()
    context.thread.join()

@fixture
def browser_chrome(context):
    # -- STEP: Setup browser fixture
    context.browser = webdriver.Chrome()
    yield context.browser
    # -- STEP: Teardown/cleanup fixture
    context.browser.quit()

fixture_registry = {
    "fixture.browser":   browser_chrome,
    "fixture.webserver": webserver,
}

# -- BEHAVE HOOKS:
def before_feature(context, feature):
    model.init(environment='test')

def before_tag(context, tag):
    if tag.startswith("fixture."):
        # USE-FIXTURE FOR TAGS: @fixture.browser, @fixture.webserver
        return use_fixture_by_tag(tag, context, fixture_registry):
```
```gherkin
# -- FILE: features/use_browser.feature
# HINT: Fixture are automatically setutp and teardown via fixture-tags.
@fixture.webserver
@fixture.browser
Feature: Use Webserver and browser
 ...
```
