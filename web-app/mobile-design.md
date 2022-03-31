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
