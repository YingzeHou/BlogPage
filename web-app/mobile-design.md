# Mobile Design

## Mobile Input

#### Capabillities:&#x20;

input & senseing, touch-sensitive screen --> direct manipulation input and multi-touch gestures

#### Direct Manipulation Input:

Web & Desktop: mouse or trackpad input mapped to screen using _relative_ mapping

Mobile: mapping is _absolute_

#### Multi-touch Gestures:

A number of idiomatic gestures --> specific function

![](<../.gitbook/assets/Screen Shot 2022-03-31 at 10.34.47 AM.png>)

1. **Tap**: Maps to a "click" on the desktop computer to select objects or to activate/toggle the state of a control
2. **Double-Tap**: Zooming in/out content, selecting items in accessibility mode, or selecting text.
3. **Long-press**: Opening contextual menus, previews of content, or enabling editing modes.
4. **Drag/Swipe**: Used to scroll through content, move objects, or adjust controls. These gestures are the most commonly used gestures on mobile devices. (Drag = swipe+hold); Also, move object on canvas & trigger OS-level actions: switch between applications
5. **Triple-Swipe**: Mapped to specific OS-level activities, e.g., undo, redo.
6. **Two-finger Pinch and Spread**: Used to shrink or expand visual elements, e.g., changing the scale of a map.
7. **Three-finger Pinch and Spread**: Mapped to OS-level actions, such as copy, cut, and paste.

#### Motion Gesture

Gestures that involve moving the mobile devide in specific ways, e.g., shaking to enable/disable silent mode. These gestures are usually application specific or customizable at the OS level.

![](<../.gitbook/assets/Screen Shot 2022-03-31 at 10.39.34 AM.png>)

## MicroInteractions

Microinteractions are contained product moments that revolve around a single use case. (Facebook like button, pull-to-refresh action, flicking a notification to dismiss it, etc.)

Process: Trigger --> Rules --> Feedback --> Loops\&Modes

1. **Trigger**: Events that initiate the microinteractions. Triggers can be manual/user-initiated or automatic/system-initiated (Manual trigger: by flipping a switch, pressing a button, speaking to the system; Auto trigger: chime when a new text message arrives, silence the phone a!er 10 pm)
2. **Rule**: Rules determine what happens (and doesn't happen) in the system when a microinteraction is triggered.
3. **Feedback**: Information that the user sees, hears, or feels to reflect what is happening. Feedback can take many forms: visual, aural, haptic, etc.
4. **Loops & Modes**: Meta-rules that, depending on context, change microinteraction rules and feedback (e.g., "snoozing" a reminder; chime/vibration feedback when silent mode is off/on) (**Loops**: Length of interaction & whether interaction repeats: related beeping when you leave the fridge door open / microwave oven reminder to pick up food changing over time)\
   (**Modes**: switch the functioning or operation of the system. E.g., "do not disturb" mode that changes system behavior)

## Mobile Design Pattern

Mobile platforms are highly constrained design environments. Mobile design patterns help designers overcome these limitations by expanding capabilities for input, display, and navigation

* **Stacks**: Used to vertically organize design elements such as a toolbar, content panes, and a navigation bar to maximally utilize the vertical space in mobile devices
* **Screen Carousels**: Full-screen content panes that can be placed on a horizontal array to display different instances of the same kind of information, such as weather information for different cities.
* **Drawers:** Drawers provide links for navigation or controls for the various settings of the application.
* **List\&Grids:** \
  **Lists** involve vertically stacking a large number of items, including text, controls, and thumbnails, and supporting navigation through **vertical scrolling**.\
  **Grids** involve a large continuous grid or multiple panes of grids that users can scroll through vertically or horizontally.\
  **Grids** are more commonly used for information with **more visual content**, such as media thumbnails, icons, and photos.
* **Carousels**: Content carousels provide a row of content items including images or textual cards that users can navigate through by swiping le! and right.
* **Swimlanes**: Swimlanes are stacked content carousels that each show a row of items, enabling visual browsing through several different lists with minimal navigation.
* **Card:** Cards are little rectangles full of images and text that serve as entry points to more detailed information. They can be organized by lists and grids, but they put together different compositions of multimedia content, including images, text, and links, on a column, row, or grid that users navigate through by swiping horizontally and vertically.
* **Bars**: These are vertical or horizontal strips containing buttons or tabs dedicated to different components or tools\
  **Tab bar**: placed at the top, bottom, or the side of the screen enable navigation between different components\
  **As Toolbars**: activate various application or operating-system-level functions\
  **Help Navigation**: linking to previously viewed content or to view the previous/next item among multiple screens
* **Search, Sorting, Filtering**: Used to enable search and filtering to navigate through a large body of content that may be distributed across the entire navigation structure of the application\
  Provide a **search box** to enter a search query either by typing text, voice input, or selecting from among a history of searches
* **Landing Pages, Guide Tour:** Includes a landing, welcome, or home screen that can serve as a portal to the most frequently used functions or as a guide to the next action in the task\
  **Help screens** by overlaying instructions or tooltips on the screen
* **Advanced Direct Manipulation:** Applications, such as image editors, drawing or presentation tools, or media players, enable direct-manipulation-based controls for content creation or editing
* **Panes & Panels:** Multi-pane structures and pop-up panels and tools are commonly used in tablets to provide secondary application windows in a way that's similar to desktop applications.
* **AR/VR:** Augmented and virtual reality, a.k.a. mixed reality, are used to overlay objects or information on images or video of the user's real environment that is captured using the mobile device's camera.

## Prototype

Building a dra! or an early version of a product or system in order to explore, demonstrate, and test design ideas for a part or the entirety of the product or system.

#### Paper Prototyping

Mocking up design ideas by sketching pages/screens with design elements using design supplies (e.g., paper, pencils, markers, scissors, glue, tape) and simulating how the envisioned system would respond to user input by swapping different pages/screens and moving/changing design elements.

#### Wireframe

Lo-fi prototypes of the makeup of a design in terms of its structural components. Wireframes can be hand-drawn or digitally created. \
Most useful in the early-to-mid stages of the design process.

#### Annotation

Labels, explanations, and notes that provide further information on the goals, content, and functioning of the design elements illustrated on wireframes.\
Key in addressing the problem of interpretability of simplified designs for all stakeholders.

#### Interactive

Creating realistic prototypes of the navigation or structural components (or both) of the design idea by creating a series of screens/pages with design elements, linking these screens/pages for navigation, and simulating the transitions between screens/pages.

#### Native prototyping

Implementing and testing design ideas on the target technology platform of the design.

{% embed url="https://reactstudio.com" %}

{% embed url="https://bootstrapstudio.io" %}
x
{% endembed %}

## Prototyping Theory

#### Three Dimensional Model of Prototyping

Prototypes represent three dimensions of a design idea:\
1\. **Role**: Represents the functions that the system serves in the user's life, i.e., how the system is useful to them.\
2\. **Look and feel**: Simulates the sensory experience of the user while using the system, i.e., what the user sees, hears, and feels during use.\
3\. **Implementation**: Includes the technical capabilities that enable the system to perform its function, i.e., the low-level details of how the system works.

There three combined: **Design Integration:** Represents the complete user experience with the system as envisioned in the conceptual design.

#### Prototyping Scope

1. **Horizental**: Provides a broad view of the entire system and focus on the user interaction rather than the functionality.
2. **Vertical:** Focuses on a single feature/functionality and provides the full functioning of that feature.

![](<../.gitbook/assets/Screen Shot 2022-04-05 at 11.37.05 AM.png>)

## Prototyping Strategy

#### Throwaway

Rapid prototyping to explore design ideas, demonstrate feasibility, communicate with stakeholders, and test the ideas with users and eventually discarding the prototype instead of further developing the model into a final product.\
Most lo-fi and paper prototypes are throwaway protototypes.\
Throwaway prototyping is usually combined with sketching.

#### Evolutionary

Also called breadboard prototyping, the design team incrementally builds prototypes of a design idea, tests the idea with users, and refines the prototype until it reaches the desired level of maturity.\
Most products we use are evolutionary prototypes that went through alpha, beta, etc. phases.

#### Incremental&#x20;

Dividing system functionality into slices (vertical prototypes) based on design specifications and incrementally building each slice that is then integrated into the overall system.\
Appropriate for large and complex projects.

#### Extreme

Breaking down the development into three phases that build on each other: (1) building a static prototype, (2) building fully functional, interactive components that will simulate services, and (3) finally implementing the services.\
Enables rapid and parallel prototyping, testing, and refinement by removing dependencies between different components of a system or between the system and third party services.

#### Fidelity of Prototyping: The more "done" the prototype looks, the narrower the feedback will be; and vice versa.

The level of detail in which a design is represented in the prototype.

1. **lo-fi advantage**:
   1. Has lower development cost
   2. Prevents designers from prematurely wedding to specific design ideas
   3. Enables exploring, communicating, and testing of conceptual designs
   4. Helps designers identify structural, navigation, and organizational issues
   5. Allows rapid evaluation of multiple design ideas
   6. Enables communication among stakeholders
   7. Allows identifying market requirements before dedicating resources to development
2. **lo-fi limitation:**
   1. Requires a facilitator to drive the prototype during testing and communication
   2. Offers limited ability to identify breakdowns in design
   3. Lacks sufficiently low-level specifications for development
   4. Provides limited sense of feasibility
3. hi-fi

![](<../.gitbook/assets/Screen Shot 2022-04-05 at 11.43.53 AM.png>)
