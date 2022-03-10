# Web Design

## Designing for Desktop

### WIMP Paradigm:

Windows, Icons, Menus, Pointers

#### Windows:

Resizable containers of individual applications

* Primary: for the main functionality, like canvas
* Secondary: main windows through modal panes, dialog boxes, etc.

#### Window Organization:

Organized in a way that overlaps several windows or tiles them across the screen

#### Window Structure:

Windows bring together dedicated panes in different configurations

* Secondary windows can be stacked, docked, and floating

#### Menus:

Menus list all the functions of an application. Menu lists serve educational and reference purpose

#### Toolbars, Palettes, Sidebars, and Tooltips

Facilitate access to frequently used functions

#### Tool Palettes (Not always shown, unlike toolbars, have to click in things to be shown)

Provide advanced controls for particular function rather than frequently accessed functions

#### Pointing

On an application canvas enables a range of advanced capabilities for direct manipulation

## Designing for Web

**Desktop:** Dynamic, persistent screens and suppporting components that enable users to perform complex tasks

**Webpages**: Interconnected pages with aids that help users to navigate and access a large body of contents

Single-page applicatoin (SPA) provides the functions of a desktop application on a webpage following the conventions of desktop applications

#### The Page

Building block of web content, use primary and secondary navigation aids

#### Primary Navigation Aids

Take the form of menus/menubars and reflect the major areas or sections of a website

#### Secondary Navigation Aids

Provide comprehensive links to specific content on the site as fat navigation (a pop window with a lot of content expanded), left-hand navigation, footer navigation, etc.

#### Get back to home

_Breadcrumbs (trace of menu clicks by the user)_ and _hierarchical lists (similar to left-hand secondary navigation, use tabs and indent to show the hierarchy)_ are solutions

#### Organizing Page Content: The Fold

The dividing line between the area that is visible when a page first loads and the remainder of the page

#### Fitting it all in

Large volumns of content is either broken into discrete pages through pagination or incrementally loaded through infinite scroll

#### Search

An alternative to page navigation, provides users with listings of content based on a search query (auto-completion, auto-correction)

#### Faceted search

Helps user narrow down a search once results are returned based on a simple query by providing functions to sort and filter

## Interaction Design

Defining behaviors for a system that engages the full spectrum of its user's perception, cognition, and movements

Differs from visual design in its closer and more complex relationship to user behavior and context

#### Five Dimensions of Interaction Design:

* 1D: Words
* 2D: Visual representation
* 3D: Physical objects and space
* 4D: Time: animation
* 5D: Behavior: reaction

### Interaction Structure

The design of the organizing principle of an interactive system.

#### Show one single thing:

Focuses on conveying info on a specific topic/facilitaiting a specific activity

key components:

* Content of the single thing
* Supporting tools that help the user act on the content

#### Show a list or set of things:

Provides rows or grids of items of the same kind that provide links to components that focus on that item.

Include design elements that organize or categorize the list (First letter, time, etc..)

#### Provide tools to create a thing:

Supporting user creation of new content, e.g., a canvas or form on which to write, draw, paint or structured form for data entry

#### &#x20;Facilitate a task

Provides collections of components or controls that help users perform specific actions, e.g., changing a setting

The designer must organize these controls in an effective and logical way

#### Combining structure

Any page/component can follow the structure of these components, thus they can be combined to create complex applications

Single-page applications (SPAs) o!en combine these structures

## Layout

Arrangement of visual elements on a canvas.

#### Creating a focal point

Center of visual interest, the design directs the atention of the viewer first.

#### Following the golden proportion

1:1.618, creates a compositional grid that suggests an asymmetrical, but balanced placement of items on a layout and produces a universal aesthetic appeal

#### Rule of thirds

Approximation of golden ratio that is easier and more flexible to use. Canvas divided by 3x3 grid, the intersections serve as focal point

#### Effectively using grids

Grids serve as visual framework for organizing elements in an orderly and balanced fashion

#### Integrating type

The use of headlines or blocks of text to guide the user's attention to messages.

#### Placing imagery

Use of imagery to create a focal point or movement on the canvas (Place on top, not bottom; direction should be toward next focal point; never flip images; do not interrupt headlines; do not wrap text around images.

#### Using negative space

Space left on the canvas from other design elements, used to provide a visual break and create balance.

#### Grouping using Gestalt Theory

Visual perception principles that predict how users will perceive design elements:

* Proximity
* Similarity
* Continuity
* Closure

#### Creating visual hierarchy

Using relative positioning and sizing to communicate what design elements are more importatn and should be looked at first

#### Exploiting visual scan pattern

Designing layouts that exploit common eye scanning patterns (F pattern / Z pattern)

#### Creating contrast and emphasis

Using contrast and emphasis to establish visual hierarchy by manipulating features of design elements, including position, size, color, typographic characteristics.

## Principle of Navigation

#### Wayfinding

User behavior where navigation across components follows a particular workflow or supports user goal:

* Signage
* Environmental clues
* Maps, site maps

#### Cost

The time and effort required by users to navigate between components:

* Min factors that increase cost of navigation: context switch, errros, delays
* Min travel time by min number of steps and context switch

#### Aid

Design element that aid users in navigating through content

* Global navigation aids: menus, tabs, sidebars
* Utility navigation aids: sign in, help, print
* Associative/in-line navigation aids: related links

#### Models

Commonly used patterns of navigation through interactive applications

* **Hub & spoke**: Involves a central hub: home screen, provides transitions to and from several specialized components
* **Fully connected**: A central component is connected to all other components that are also linked to each other.
* **Multi-level**: Involves main components that are fully connected with each other and _sub-components_ that are only connected among themsleves
* **Step-wise**: Follows a sequential or branching navigation that represents step-by-step process: google form, checkout at e-commerce website
* **Pyramid**: Similar to the stepwise model, but at each step, the user can navigate to the hub and back
* **Pan-and-zoom**: Provides users with the ability to continuously navigate across a large space of content: map, list, written document
* **Flat-navigation**: Involves a central workspace that is always visible and functions that do not require context switches or navigation
* **Modal panel:** Follows the flat navigation model except for modal dialogs that are temporarily overlaid on the canvas to help the user perform specific functions
* **Clear entry points**: Complex applications involve navigational models with clear entry points that guide the user to frequently used or temporary functions without having to go through the hierarchical structure or a step-by-step process.
* **Bookmarks**: Bookmarks allow users to conveniently navigate to a point of his choice, anytime he wants, even if it's deep inside a navigational structure. These give people a way to avoid traversing many links to get to a desired page or state
* **Escape hatch**: Provide users with the ability to go back to the main component, home page without having to trace steps back.

## Design Paradigms

An archetypal solution or an approach to solving design problems.

### Implementation Centric

Interaction design maps directly to how system functions are implemented

**Pros:**

1\. Very easy to build, easy to debug, easy to troubleshoot

#### **Cons:**

1\. Requires learning how the functions work

2\. Requires skills in using the functions

3\. The system cannot perform high-level actions

### Metaphorical Desgin

Following a real-world metaphor that users are expected to be familiar with.

### Global Metaphor

A global metaphor provides a single, overarching framework for all the metaphors in the system (e.g., Magic Cap).

#### Pros:

They work well in expert interfaces where the interface simulates a real-world system

#### Cons:

Inability to scale; lack of familiar real-world system for entirely new capabilities; cultural differences; inability to adapt as capabilities evolve

### Idiomatic Design

Building dedicated, highly expressive interaction capabilities that users must learn.

Example: Mouse of the computer, easy to learn, even though not exist in real world

* **Primitives**: atomic actions, like point, click
* **Compounds**: complex actions, like double-click
* **Idiom**: higher-level element, like deleting text

## Affordances

The perceived properties of a design element that give clues about how to interact with it. Designers have borrowed the concept from ecological psychology.

![](<../.gitbook/assets/Screen Shot 2022-03-08 at 11.37.17 AM.png>)Affordance can be hidden or false

* **False affordance**: An action that is perceived by the user but in fact doesn't work as expected
* **Hidden affordance**: The affordance is not too obvious
* **Perceptible affordance**: An object's characteristic imply an action

## Design Pattern

A design pattern is a general, reusable solution to a commonly occurring problem within a given context.

![](<../.gitbook/assets/Screen Shot 2022-03-08 at 11.46.39 AM.png>)

#### Pros:

1. Reduce design time and effort
2. Improving the quality of design solutions
3. Establishing familiarity across systems
4. Providing a baseline or state of the art

#### Cons:

1. Not every design problem will warrant a pattern
2. Patterns may not exist for new design spaces

## Design Language

### Enter Pattern Language

A complete and hierarchical collection of patterns for a family of design problems

Patterns are words (components) that are connected with grammar rules to make sentences (screens) and eventually language (user experience)

#### Posture-level pattern

The structure that an application follows: type of app (e-commerce? social media? portfolio?)

* Structure
* Component
* User experience
* Alternative/Competitors

#### Experience-Level Pattern

The user goals that make up the user experience that the app supports (activity tracking, coaching, reviewing...)

* Primary goal
* Secondary goal ...

#### Task-Level Pattern

Design solutions that help users accomplish sequences of actions that mke up user tasks (loggin a meal, capturing a run....)

#### Action-Level Pattern (Widget or Component)

Design solutions that support the actions taken to complete the steps of the user task (start button to initiate activity tracking, list entry for food item)

#### Simplified model:

1. Context: Type of app
2. Flow: Component that support specific functions
3. Implementation: Visual/Behavioral element

## Usability Evaluation

The assessment of the effectiveness of and user satisfaction with desgin solutions

**1.Testing-based methods**:

Empirical, based on data, testing with users who represent the target population of design solutions.

**2. Expert-review-based methods:**

Usability inspection, review-based evaluation by experts who follow well-established protocols to inspect the usability of design solutions

### Heuristic Evaluation:

Involve having a small set of evaluators examine the interface and judge its compliance with recognized usability principles (heuristic)

* **Visibility of system status**: Keep user informed with feedback at reasonable time
* **Match between system and the real world**: Speak the users' language, with words, phrases and concepts familiar to real world conventions
* **User control and freedom:** Choose system functions by mistake and will need clearly marked "emergency exit" to leave the unwanted state, like redo and undo
* **Consistency and standards:** Should not make user wonder whether different words, situation, or action means the same thing (click turn blue, and click turn red is inconsistent)
* **Error prevention:** Eliminate error-prone conditions or check for them and present users with a confirmation option before they commit to the action (Google auto correction when search)
* **Recognition rather than recall**: Minimize user memory load by make options visible. User should not need to remember info from one part of dialogue to another.
* **Flexibility and efficiency of use:** Accelerators may often speed up the interaction for the expert user, catering both inexperienced and experienced users (keyboard shortcut)
* **Aesthetic and minimalist design:** Dialogue should not contain information which is irrelevant or rarely needed.
* **Help user recognize, diagonose, and recover from errors**: Error message be in plain language, precisely indicated the problem, and suggest a solution (Incorrect password reminder)
* **Help and documentation**: Provide documentation for user to easily search around and understand (Word explanation of HELP CENTER icons)

#### How many evaluators are needed? 3\~5

`ProblemsFound(i) = N(1-(1-l)^i)`

i: independent evaluators

N: total number of usability problems in the interface

l: the proportion of all usability problems found by a single evaluator

#### Heuristic Evaluation Reporting

A document that highlight top problems and with solutions

Severity Ratings: 0\~4 rating scale

### Cognitive Walkthrough

Specialist assesses the learnability and discoverability of a design by posing and answer questions

* Will the user try and achieve the right outcome?
* Will the user notice that the correct action is available to them
* Will the user associate the correct action with the outcome they expect to achieve?
* If the correct action is performed, will the user see that progress is being made towards their desired result?





