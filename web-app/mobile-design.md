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

## Design for Accessibility

Usability: The effectiveness, efficiency, and satisfaction with which a specified set of users can achieve a specified set of tasks in a particular environment.

Accessibility: The usability of a product, service, environment, or facility by people with the widest range of capabilities. (Used by as many people as possible, focus on disability)

### Disability

A disability is any condition of the body or mind (impairment) that makes it more difficult for the person with the condition to do certain activities (activity limitation) and interact with the world around them (participation restrictions).

#### Impairment:

In a person’s body structure or function, or mental functioning (e.g., loss of a limb, loss of vision, or memory loss)

### Anotomical

* **Sensory impairment**: Involves impairment in one or more senses, such as loss of vision or hearing.
* **Physical impairment:** Involves loss of function to one or more parts of the body, e.g., congenitally or a!er stroke or spinal-cord injury.
* **Cognitive impairment:** Includes cognitive deficits, such as learning impairment or loss of memory/cognitive function due to aging or conditions such as Alzheimer's disease.
* **Visual Disability**: Impairments in vision, including low vision, blindness, and color blindness.
* **Motor/Mobility**: Muscular or skeletal impairments in the hands or arms that affect user input as well as impairments that affect mobility, where users are in a wheelchair or bedridden.
* **Auditory**: Deficits that affect hearing at different levels of severity, including deafness.
* **Seizure**: Neurological impairments, such as photosensitive epilepsy, that result in sensitivity to light, motion, and flickering on screen, which might trigger seizures
* **Cognitive/Learning**: Congenital, developmental, and traumatic (e.g., traumatic brain injury) conditions that result in cognitive or learning challenges

### Temporal

* **Permanent impairment:** Congenital or long-term conditions, such as color blindness, missing body parts, etc
* **Temporary impairment**: Impairments that improve over time, such as recovery a!er illness or accidents, e.g., a broken arm.
* **Situational impairment**: Impairments introduced by context, such as environments with low light or noise.



#### Limitation in activities:

(e.g., difficulty seeing, hearing, walking, or problem solving)

#### Restriction in participation:

In activities of daily living (e.g., working, engaging in social and recreational activities, and obtaining health care)

![](<../.gitbook/assets/Screen Shot 2022-04-07 at 10.12.34 AM.png>)

### Achieve accessibility?

## Accessibility Design

![](<../.gitbook/assets/Screen Shot 2022-04-07 at 10.14.18 AM.png>)![](<../.gitbook/assets/Screen Shot 2022-04-07 at 10.14.24 AM.png>)

#### Mismatch between ability and environment

Context-dependent disability results from a mismatch between abilities and the environment:\
Ability + Context = Disability

#### Universal Design:

The design of products and environments to be usable by all people, to the greatest extent possible, without the need for adaptation or specialized design.

Design solutions that benefit some individuals may benefit the whole society. E.g., in the US, only 26K people are suffer loss of upper extremities. \
Designs that would benefit these 26K would also benefit another 21M people with temporary or situational disabilities.

### Principle of Universal Design:

* **Equitable use**: \
  The design is useful and marketable to people with diverse abilities.\
  1\. Provide the same means of use for all users: identical whenever possible; equivalent when not.\
  2\. Avoid segregating or stigmatizing any users. \
  3\. Provisions for privacy, security, and safety should be equally available to all users. \
  4\. Make the design appealing to all users.
* **Flexibility in Use:**\
  The design accommodates a wide range of individual preferences and abilities.\
  1\. Provide choice in methods of use.\
  2\. Accommodate right- or le!-handed access and use.\
  3\. Facilitate the user's accuracy and precision.\
  4\. Provide adaptability to the user's pace.
* **Simple and Intuitive Use**:\
  Use of the design is easy to understand, regardless of the user's experience, knowledge, language skills, or current concentration level.\
  1\. Eliminate unnecessary complexity.\
  2\. Be consistent with user expectations and intuition.\
  3\. Accommodate a wide range of literacy and language skills.\
  4\. Arrange information consistent with its importance.\
  5\. Provide effective prompting and feedback during and a"er task completion.
* **Perceptible Information**:\
  The design communicates necessary information effectively to the user, regardless of ambient conditions or the user's sensory abilities.\
  1\. Use different modes (pictorial, verbal, tactile) for redundant presentation of essential information.\
  2\. Provide adequate contrast between essential information & surroundings. \
  3\. Maximize "legibility" of essential information\
  4\. Differentiate elements in ways that can be described (i.e., make it easy to give instructions or directions). \
  5\. Provide compatibility with a variety of techniques or devices used by people with sensory limitations.
* **Tolerance for Error**:\
  The design minimizes hazards and the adverse consequences of accidental or unintended actions.\
  1\. Arrange elements to minimize hazards and errors: most used elements, most accessible; hazardous elements eliminated, isolated, or shielded.\
  2\. Provide warnings of hazards and errors. \
  3\. Provide fail safe features. \
  4\. Discourage unconscious action in tasks that require vigilance.
* **Low Physical Effort**:\
  The design can be used efficiently and comfortably and with a minimum of fatigue.\
  1\. Allow user to maintain a neutral body position.\
  2\. Use reasonable operating forces.\
  3\. Minimize repetitive actions.\
  4\. Minimize sustained physical effort.
* **Size and Space for Approach and Use**:\
  Appropriate size and space is provided for approach, reach, manipulation, and use regardless of user's body size, posture, or mobility.\
  1\. Provide a clear line of sight to important elements for any seated or standing user.\
  2\. Make reach to all components comfortable for any seated or standing user.\
  3\. Accommodate variations in hand and grip size.\
  4\. Provide adequate space for the use of assistive devices or personal assistance.

## Assistive Technology

Specialized tools that close accessibility gaps

* **Screen Reader:** Software used by individuals with vision impairments to read screen content
* **Screen Magnification:** Enlarges text or graphics on screens to improve visibility of content for individuals with limited vision.
* **Text Reader**: Tools that read out loud text on screens to support vision and learning disabilities.
* **Braille for the Web**: A mechanical device that translates textual content on the screen into Braille.
* **Alternative Input Device**: Specialized tools that help individuals with motor impairments who cannot use a mouse or keyboard with pointing. (Head/Mouth wands/pointer, Motion/eye tracking, speech input, etc)

### Accessibility Testing

{% embed url="http://wave.webaim.org" %}

{% embed url="http://colororacle.cartography.ch/index.html" %}

{% embed url="http://juicystudio.com/services/image.php" %}

## Conversational Interface

Why conversational interface brings value?

1. Streamlining app installation, login, payment, notifications, and and so on in a conversational paradigm.
2. In some contexts, e.g., while driving, CIs are more effective, efficient, and satisfactory due to resource constraints.
3. CIs address many accessibility problems, including vision (e.g., blindness), motor (e.g., tremor), and cognitive (e.g, dyslexia) deficiencies.

### Design Principles

#### Gricean Maxims

Proposed by Paul Grice, conversations follow the cooperative principle and four key maxims:

* Maxim of quality (truthful and accurate communication)
* Maxim of quantity ( just the right amount of information)
* Maxim of relevance (appropriate and relevant information)
* Maxim of manner (clear, cooperative communication)

#### Multimodality

Multimodal interfaces utilize multiple modalities, including visual information, speech, touch, and so on, in user experiences they afford.

* Take advantage of other modalities, e.g., visual information, vibrations, etc., wherever appropriate
* Provide users with breaks for decision making, interruptions, etc.

#### Interaction Paradigm

Conversational interfaces can follow different paradigms depending on the context of use and the design of the application:

*   Command-and-control interfaces (always-on voice assistants)

    **Interfaces where speech input is mapped to specific system functions that are called immediately. These interfaces commonly utilize:**

    * Expressing user intent using a wake word (e.g.,"OK, Google") or the pressing of a button (e.g., home button in the iPhone)
    * Indicating listening and understanding
    * Executing the mapped function
*   Conversational interfaces (chatbots, task assistants, social robots)

    **Interfaces where the interaction with the system has the characteristics of human conversations, including turn taking, theoretically infinite depth, conversational markers, etc.**

#### Turn talking

Speaking turns are the core, cooperative structure of conversations that involves one speaker at a time and an explicit exchange of tokens:

* One speaker at a time — transparency in who is speaking
* Turn exchanges — explicit signaling of who will speak next
* Interruption handling — very difficult with CIs

#### Conversational Markers

Speech cues that indicate the state or the direction of the conversation. Types of conversational markers:

* Timelines ("First," "Halfway there," "Finally")
* Acknowledgements ("Thanks," "Got it,", "Alright," "Sorry about that")
* Positive feedback ("Good job," "Nice to hear that")

#### Confirmation

CIs are designed with explicit forms of confirmation to improve system usability and transparency.

* Explicit Confirmation: Requiring the user to confirm: "I think you want to set a reminder to 'buy insurance before going skydiving next week.' Is that right?
* Implicit Confirmation: Letting user know what was understood: "Ok, setting a reminder to buy insurance..."

#### Error Handling

Deviations from expected conversational flow due to technical mistakes, unexpected user behavior, environmental influences, etc.

* No speech detected
* Speech detected, but nothing recognized
* Something was recognized correctly, but the system does the wrong thing with it
* Something was recognized incorrectly

![](<../.gitbook/assets/Screen Shot 2022-04-12 at 10.22.01 AM.png>)

## Usability Heuristic for CI

Developed by Jacob Nielsen, heuristic evaluation involves having a small set of evaluators examine the interface and judge its compliance with recognized usability principles (the "heuristics").

1. **General Heuristic**
   1. Give the agent a persona through language, sounds, and other styles.
   2. Make the system status clear.
   3. Speak the user’s language.
   4. Start and stop conversations.
   5. Pay attention to what the user said and respect the user’s context.
2. **Conversational Style**
   1. Use spoken language characteristics.
   2. Make conversation a back-and-forth exchange.
   3. Adapt agent style to who users are, how they speak, and how they are feeling.
3. **Guiding, Teaching, and Offering help**
   1. Guide users through a conversation so they are not easily lost.
   2. Use responses as a way to help users discover what is possible.
4. **Feedback and Prompts**
   1. Keep feedback and prompts short.
   2. Confirm input intelligently.
   3. Use speech-recognition system confidence to drive feedback style.
   4. Use multimodal feedback when available.
5. **Errors**
   1. Avoid cascading correction errors.
   2. Use normal language in communicating errors.
   3. Allow users to exit from errors or a mistaken conversation.

## VUI Design Context

### DialogFlow

A development suite for conversational interfaces for websites, mobile applications, and IoT devices (e.g., smart speakers)

#### Conversational Interface

User interfaces that use human dialogue as the primary mode of human-computer interaction.

#### Why hard to prototype human language? Because...

Social interactions are driven by tacit knowledge: Knows more than what we talk

#### Solution: Experience Prototyping

Prototyping the holistic experience of interacting with a product

**An experience prototype is any kind of representation, in any medium, that is designed to understand, explore or communicate what it might be like to engage with the product, space, or system we are designing.**

#### **When to use Experience Prototyping?**

1. Understanding existing user experiences and context
2. Exploring and evaluating design ideas
3. Communicating ideas to an audience

#### What do we prototype?

1. System behavior
2. User behavior
3. Interactions with context

### Steps to do experience prototyping

1. **Define Context:** E.g. passengers using entertainment system on a bus, travelers packing their luggage
2. **Develop Scenario:** E.g. buying a ticket, users packing, cooking a meal.
3. **Identify Design Goal:** E.g. find, filter, and purchase flights; help the user set and follow personal goals through daily reminders.
4. **Set up an environment:** E.g. creating props to represent devices, environmental constraints.
5. **Act out interactions:** E.g. How will the interaction unfold? How will the user behave? How should the system behave**?**
6. **Develop Insight:** E.g. What did you learn about system behavior, user behavior, and interactions with context?

#### BodyStorming

Bodystorming is a creativity method that involves physically experiencing a situation to develop new ideas and insights.

Supporting design teams in ideating and acting out human-robot interactions using a system called Synthé.



