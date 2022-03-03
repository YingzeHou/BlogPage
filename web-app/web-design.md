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
