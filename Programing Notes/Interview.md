# Soft Skills

- Greatest Strength
    - Analytical & Learning I enjoy analyzing different aspects of a software solution and learn about the inner-workings.
- Weakness 
    - Explaining technical issue to non-technical person.
- Proudest Achievement in your career
    - AWS Certification
    - Nexus HRIS || TrackR - Fullstack application from the ground up which implements security, data retention, users, and CRUD operations.
- Why should we hire you for this position?
    - Frontend:
        - As a frontend developer with a focus on React, I have a passion for creating beautiful and functional web applications. I am always learning and staying up to date on the latest best practices and technologies, and am excited to bring my skills and experience to your team.
    - Backend:
        - As a backend developer with a focus on .Net, I have a passion for creating beautiful and functional backend applications. I am always learning and staying up to date on the latest best practices and technologies, and am excited to bring my skills and experience to your team.
    - Fullstack:
        - As a fullstack developer with a focus on React & .Net, I have a passion for creating beautiful and functional web applications. I am always learning and staying up to date on the latest best practices and technologies, and am excited to bring my skills and experience to your team.
- How do you prioritize your tasks when you have multiple deadlines to meet?
    - Put your head down and get to work. Stressing about it gets you no where.
    - Use your calendar. Its important to set time apart on your calendar to focus on nothing but getting things done. 
    - Communicate: Its important to both ask for assistance and let others know of the issue.
- How do you explain new topics to coworkers unfamiliar with them?
    - First I try to understand their level of technical understanding and the level they need to understand the technical solution.
    - I try to find a common denominator something that both of understand. A metaphor of sorts.
- Questions to ask interviewer
    - "What brought you to this company? What has been most challenging for you?"
    - 
- Stories

||Situation |Action |Result |
|---|---|---|---|
Working on Console HRIS| It was a three man team, two of us had significant previous tech experience. Our last teammate didn't and was struggling on how to turn lessons into an actual product.  |The three of us sat down together and worked through the first few classes together explaining why we were taking certain actions. 2. I provided him with resources that I used in the past. 3. We encouraged him to work on a few of the functions himself providing code review. |We ended up creating the highest scoring project. |
HackerRank HCL| While in the training period at HCL they had regularly gave a test covering Spring and up to that point I had only used Java alone.  I bombed the test, and failed all five unit tests. | 1. I obtained a copy of the tested code.2. I studied it deeply learning how the tests worked and how to implement the functions.  3. I set up a 1:1 meeting with the test creator and showed them how to improve the test cases so they didn't rely on each other.|They implemented the new tests, and allowed me and others to retake it. |
SAP Training| During a large project, twenty or so people were required to upskill in SAP. HCL hired an consultant to train us in SAP CPI. The problem came in because the training was subpar. | The technology was something I had a grasp on, so I assisted others in the team who struggled at grasping the technology. Me and one other would regularly stay late to assist our teammate with hands-on learning.|It ended with everyone trained in the technology, and the project itself went smoothly due to the use of SAP CPI |
Design Page Bug |Two pages with "the same" link were returning similar but different results. |I noticed that the webpages were using file routing. Checking the codebase I found that my assumptions were correct, noticing a markdown file at design.md and design/index.md. |In the end I used JS to redirect from one url to another therefore only one file would have to be kept updated, and any links created in the past wouldn't break. |

# Technical 

- Projects you're proud of?

|Common Questions |Nexus HRIS |Zenith-UI |TrackR | Console HRIS*
--- | --- | ---| --- |
|Challenges | Front-end Design, First fullstack-application | Building Generic Front-End Components | N/A
|Mistakes/Failures | Overconfidence with my weak points like design, Built out front end first.  | Note enough planning | N/A
|Enjoyed | Figuring out how each aspect of the application works together. Previously I only worked on either the front end or the backend. |Learning how to build more reusable React components. | N/A
|What you'd do differently | Collaborate with designers for a better look and feel. Build out the backend first. Use GraphQl rather than REST. | Put a lot more planning into the project. Learn to optimize the size of the package. | N/A



- What is an abstract class, and why would you use it?
    - An abstract class is a class that contains abstract methods. These methods have declarations but no implementations. Instead, they’re implemented by sub-classes of the abstract class, which makes them more flexible and easier to customize.
- Dependency Injection: A technique whereby one object (or static method) supplies the dependencies of another object.
    - Dependency: When class A uses some functionality of class B, then its said that class A has a dependency of class B.
    - Transferring the task of creating the object and directly using the dependency.
    - It makes you classes independent of their dependencies. 
    - Example: If you have a computer class that has the dependency of processor you can swap between 32-bit, 64-bit and ARM at runtime rather than compile.
    - Types of DI
        - Constructor injection: the dependencies are provided through a class constructor.
        - Setter injection: the client exposes a setter method that the injector uses to inject the dependency.
        - Interface injection: the dependency provides an injector method that will inject the dependency into any client passed to it. Clients must implement an interface that exposes a setter method that accepts the dependency.
    - Responsibility of DI 
        - Create the objects
        - Know which classes require those objects
        - Provide them all those objects
    - Benefits
        - Helps in Unit testing.
        - Boiler plate code is reduced, as initializing of dependencies is done by the injector component.
        - Extending the application becomes easier.
        - Helps to enable loose coupling, which is important in application programming.
    - Disadvantages
        - It’s a bit complex to learn, and if overused can lead to management issues and other problems.
        - Many compile time errors are pushed to run-time.
        - Dependency injection frameworks are implemented with reflection or dynamic programming. This can hinder use of IDE automation, such as “find references”, “show call hierarchy” and safe refactoring.
- A Content Management System (CMS) enables developers to define content structure and templates to provide consistency and good design while making it easy for a non-technical content owner to manage the actual content.

## General

- Don't Repeat Yourself (DRY)

### Inversion of Control

- A class should not configure its dependencies statically but should be configured by some other class from outside.
- The concept behind Dependency Injection
- The fifth principle of SOLID
    - A class should depend on abstraction and not upon concretions. In simple terms a class should not be hard-coded.
- A class should concentrate on fulfilling its responsibilities and not on creating objects that it requires to fulfill those responsibilities. 
- 

### Imperative vs Functional Programming Styles.

To Be Written

### Software Development Lifecycle

- Requirement Analysis - Analysis the requirements set in place by the stakeholders.
    - Answer: What problems need to be solved?
- Planning - Plan out the software you're looking to build. Cost, benefits, risk mitigation factors, and expected values.
    - What do we want to do?
- Architecture/Software Design - In short, you need to decide what you are optimizing for and design for that.
    - How do we reach our goal?
- Software Development - Build phase in which you seek not to answer questions but to produce outputs.
    - Let's build
- Test - Probe deeply to find errors that will slow down the release of your final product. Ensure strong fundamentals.
    - Let's ensure what we've built works
- Deployment - Listen to users and iterate because through user feedback surveys and guidance you can start again at phase one scoping new requirements.
    - Let's take our solution and use it.
    
### Object Oriented Programming (OOP) Principles 

- Abstraction
    - Hide away implementation details.
    - Create reusable, simple to understand  and easily changeable codebase by abstracting away certain details.
    - Every developer doesn't need to know how everything works just how to use it.
    - Example: You don't know how a coffee machine works. You just know how to hit the "Make Coffee" button,
    - Example 2: You don't know the exact implementation of how starting your car works, just that you need to turn the key.
- Encapsulation
    - Definition: The action of enclosing something in or as if in a capsule.
    - Also referred to as data hiding.
    - Each object should control its own state.
    - Allows developers to hide certain aspects of their code such as an object's field or property.
- Inheritance
    - Allows one object to inherit the properties and methods of another. 
    - Reusability is the key benefit of inheritance.
    - Keep your inheritance simple to understand and predictable.
    - Liskov Substitution principle: Objects of a superclass should be replaceable with objects of a subclass. Basically, subclasses shouldn't remove any fields or methods. If Dog class inherits from Animal Class then anywhere Animal is used should be able to be replaced by Dog.
    - Example: Teacher and Janitor classes both inherit from the the Person class because they all use the Name, DOB, email, and phone fields.
- Polymorphism
    - Definition: The condition of occurring in several different forms.
    - Subclasses should be able to override methods from their superclass.
    - If both `Cat` and `Dog` inherit from `Animal` the function `MakeNoise` should execute differently if `Cat` calls it then if `Dog` calls it.
    - Both method overriding and method overloading are examples of polymorphism.

### Solid Principles 

Purpose is to create understandable, readable, and testable code that many developers can collaboratively work on.
- Single Responsibility 
    - A class should do one thing and therefore it should have only a single reason to change.
    - Only one potential change (database logic, logging logic, and so on.) in the software’s specification should be able to affect the specification of the class.
    - A data container, like a Book class or a Student class, and it has some fields regarding that entity, it should change only when we change the data model.
- Open-Closed
    - Classes should be open for extension and closed to modification.
    - Modification means changing the code of an existing class, and extension means adding new functionality.
    - We should be able to add new functionality without touching the existing code for the class.
    - Avoid touching the tested and reliable production code if possible.
- Liskov Substitution
    - Objects of a superclass should be replaceable with objects of a subclass. Basically, subclasses shouldn't remove any fields or methods.
    - Given that class B is a subclass of class A, we should be able to pass an object of class B to any method that expects an object of class A and the method should not give any weird output in that case.
    - Example: If Dog class inherits from Animal Class then anywhere Animal is used should be able to be able to be replaced by Dog.
- Interface Segregation
    - Separating the interfaces
    - Many specific interfaces are better than few general interfaces.
    - Clients should not be forced to implement a function they don't need.
    - Similar to single responsibility principle.
    - Example: An interface for a parking garage should not include both functionality logic (Parking, unparking, lifting gate, etc ) and payment logic. In case a implementation of the parking garage doesn't charge for parking.
- Dependency Inversion
    - Classes should depend on abstract classes and interfaces rather than concrete classes.
    - If the OCP states the goal of OO architecture, the DIP states the primary mechanism

### Agile

- Agile is an iterative approach to project management and software development that helps teams deliver value to their customers faster and with fewer headaches.
- Works in small, but consumable increments.
- Manifesto 
    - Individuals and interactions over processes and tools
    - Working software over comprehensive documentation
    - Customer collaboration over contract negotiation
    - Responding to change over following a plan
- 12 Principles of Agile
    - Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.
    - Welcome changing requirements, even late in  development. Agile processes harness change for  the customer's competitive advantage.
    - Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale.
    - Business people and developers must work together daily throughout the project.
    - Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.
    - The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
    - Working software is the primary measure of progress.
    - Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
    - Continuous attention to technical excellence and good design enhances agility.
    - Simplicity--the art of maximizing the amount of work not done--is essential.
    - The best architectures, requirements, and designs emerge from self-organizing teams.
    - At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.
- User stories can be used to describe the work from a customer point of view.
    - `As < type of user >, I want < a goal > so that < a reason>`
    - Example: As a Teller, I want to be able to find my clients by last name so that I can locate my clients faster.
    - By adding clear, measurable results to the user story, the outcomes can be clearly measured, and you know when you are done.
- Initiatives: A collection of epics that drive toward a common goal.
- Epic: A large body of work that can be broken down into a number of smaller tasks (stories).
- Story: Short requirements or requests written from the perspective of an end user.

#### SCRUM

- Scrum is an agile project management framework that helps teams structure and manage their work through a set of values, principles, and practices.
- A product is built in a series of iterations called sprints that break down big, complex projects into bite-sized pieces.
- Agile is a set of principle and Scrum is a framework to get s#*t done
- Do
    - Make sure the team sets and understands the sprint goal and how success will be measured. This is the key to keeping everyone aligned and moving forward toward a common destination.
    - Do ensure you have a well-groomed backlog with your priorities and dependencies in order. This can be a big challenge that could derail the process if it’s not properly managed.
    - Ensure you have a good understanding of velocity, and that it reflects things like leave and team meetings.
    - Do use the sprint planning meeting to flesh out intimate details of the work that needs to get done. Encourage team members to sketch out tasks for all stories, bugs, and tasks that come into the sprint.
    - Leave out work where you won’t be able to get the dependencies done, like work from another team, designs, and legal sign-off.
    - Finally, once a decision or plan is made, make sure someone captures that information in your project management or collaboration tool, like your Jira tickets. That way, both the decision and the rationale are easy for everyone to see later.
- Don't
    - Don’t pull in too many stories, overestimate velocity, or pull in tasks that can’t be completed in the sprint. You don’t want to set yourself or your team up for failure.
    - Don’t forget about quality or technical debt. Make sure to budget time for QA and non-feature work, like bugs and engineering health.
    - Don’t let the team have a fuzzy view of what's in the sprint. Nail it down, and don’t focus so much on moving fast that you forget to make sure everyone’s moving in the same direction.
    - Also, don’t take on a large amount of unknown or high-risk work. Break down stories that are large or have high uncertainty, and don't be afraid to leave some of that work for the next sprint.
    - If you hear concerns from the team, whether it’s about velocity, low-certainty work, or work they think is bigger than what they estimated, don’t ignore it. Address the issue, and recalibrate when necessary.
- 

##### Sprints

- Set period of time where all work is done.
- A sprint is a short, time-boxed period when a scrum team works to complete a set amount of work.
- Sprints are at the very heart of scrum and agile methodologies, and getting sprints right will help your agile team ship better software with fewer headaches.  
- Sprints help teams follow the agile principle of delivering working software frequently.
- Automate your sprints.

##### Backlog

- A prioritized list of work for the development team that is derived from the roadmap and its requirements.
- The most important items are shown at the top of the product backlog so the team knows what to deliver first.
- Backlog Grooming: Product owners should update the product backlog before every iteration(scrum planning) meeting.
- Large backlogs should be broken down into short-term and long-term.
- 

##### Scrum Ceremonies

###### Sprint Planning

- An event in scrum that kicks off the sprint.
- Determine:
    - Length of sprint
    - Goal of sprint
    - Where you're going to start
- Bad sprint plans can derail the team by setting unrealistic expectations.
- Purpose:
    - The What: The product owner describes the objective of the sprint and what backlog items contribute to that goal.
    - The How: The development team plans the work necessary to deliver the sprint goal.
    - The Who: You cannot do sprint planning without the product owner or the development team. The product owner defines the goal based on the value that they seek. The development team needs to understand how they can or cannot deliver that goal. If either is missing from this event it makes planning the sprint almost impossible.
    - The Inputs: A great starting point for the sprint plan is the product backlog as it provides a list of ‘stuff’ that could potentially be part of the current sprint. The team should also look at the existing work done in the increment and have a view to capacity.
    - The Outputs: The most important outcome for the sprint planning meeting is that the team can describe the goal of the sprint and how it will start working toward that goal. This is made visible in the sprint backlog.
- TimeBox is the maximum amount of time a sprint planning meeting should last. 
- A good rule of thumb is 2 hours per week of planning. A two-week sprint planning shouldn't last longer than 4-hours.
- T-Shirt Sizing :
    - A form of relative estimations. 
    - Instead of using numbers you use t-shirt sizes for estimation.
    - Range from extra small to XXL.
    - 
- The goal of sprint planning is to establish "just enough" to last until the next sprint.

###### Sprint Review

- A time to showcase the work of the team.
- Typically 45 minutes per week of iteration

###### Sprint Retrospect

- A meeting to review what was successful during the sprint and what can be improved upon.
- Typically 45 minutes per week of iteration

#### Kanban

### Git

## C# / .Net

- Using: Import custom files (classes, interface, etc) and third-party libraries.
    - You can use the `using` statement to ensure an unmanaged resource is disposed even when an exception is thrown. `using (ObjectWithUnmanagedResources thing = new())`.
- Namespace: An address to identify a type.
- LINQ: Language Integrated Query allows you to write query for collects such as Lists.
- Access Modifiers:
    - `public`: Can be accessed anywhere
    - `private`: Can only be accessed in current type
    - `protected`: Can be accessed in current type and any type that inherits it.
    - `internal`: Can be accessed inside the type and any type in the same assembly (DLL/EXE).
- `static`: Belongs to the type itself rather than to a specific object.
- Interfaces are a way to implement standard functionality and connect different types to make new things.
    - If a type implements an interface, then it is making a promise to the rest of .NET that it supports specific functionality. Therefore, they are sometimes described as contracts.
- Stack vs Heap
    - Stack memory is faster to work with, but limited in size.
    - Heap memory is slower but theoretically unlimited.
    - Value types are located in stack.
    - Reference types are located in heap.
    - The reference number is stored on the stack but value is stored on the heap.
- What's the difference between `string` and `String`?
    - Fundamentally there is no difference since `string` is a keyword with references `System.String` aka `String`. However, it's best practice to rely on the keyword over the type because the type requires you to import the namespace.
- Describe .Net Standard
    - .Net Standard is similar to HTML5 as its a standard platform should support, but .Net Core, .Net Framework, and Xamarin implement it differently. 
- What are the different .Net Versions
    - .Net Framework
    - .Net Core
    - .Net
    - Xamarin ?
- 

## Hyper Text Markup Language & Cascading Style Sheet

### HTML
- HTML element consist of opening, closing tag and content in between.
- Block vs Inline
    - A block-level element always starts on a new line, and the browsers automatically add some space (a margin) before and after the element.
    - An inline element does not start on a new line.
    - An inline element only takes up as much width as necessary.
- Purpose of JS in HTML.
    - Without JS HTML pages are static. If HTML is the bones, and CSS is skin then JS is actions such as breathing, eating, etc.
- What leads to differences between an HTML5 specification and the browser’s interpretation?
    - HTML5 is a rule set. Its a standard and different browsers implement it differently.
- What do you use the new header and footer elements for in HTML5?
    - The header and footer elements are semantic elements that are used to provide information to the top and bottom of the webpage.
    - Header element may include navigation, logo, etc.
    - Footer element may include full list of links, copyright, etc.

### CSS
- Box model 
    - Height/Width: Content
    - Padding
    - Border
    - Margin
- Advantages
    - Separation of Files
    - Bandwidth
- Disadvantages
    - Selectors: Not all browsers support all selectors
- Include CSS with `<link>` tag
- Types of selectors
    - `*` Universal 
    - `div` Element
    - `#` ID 
    - `.` Class
 
## JS & TS

- Functions
    - Arrow Functions bind this to where it was defined. 
    - Functions bind to where it was called.
    - Arrow functions can’t be used as a constructor.
- DOM: Document Object Model refers to the entire user interface of a web application as a tree data structure.

### Array Functions

- Map
    - Maps through every element in an array. Allows you to apply a function to every element in an array, creating a new array.
- Filter
    - Takes each element of the array and applies a conditional statement. If the statement returns true, the element gets pushed to the output array.
- Reduce
    - Reduces an array of values down to just one value.
    - Accumulator: The returned value of the previous iteration.
    - Current Value: The current item in the array

## React

- What is React, and how is it different from other JavaScript frameworks?
    - First off, React is a JS Library. This is key because it means you can continue to use other JS libraries
    - React is a UI library that helps developers create dynamic, responsive, and performant websites.
- JSK: JavaScript XML its a way to write your JS alongside HTML. In reality, it’s a syntactic sugar that complies down to React.CreateElement().
- Class vs className: Class is a keyword in JS. Once the jsx is compiled down to JS if you used class it would think you were trying to define a class.
- React data flow is unidirectional
- Virtual DOM: A duplication of the actual DOM. React compare changes with the virtual DOM to increase performance. However, it causes increased memory consumption.
- What are the three main phases of a React component’s lifecycle?
    - Initial Rendering
        - Component is about to modify the DOM
    - Updating
        - After the component is added to the DOM and only updates when its state or props change.
    - Unmounting
        - When the component is destroyed and removed from the DOM.
- Synthetic Events
- Where is using a key prop necessary, and why?
    - When you're mapping through an array it is important to include a unique key prop. 
    - This is important for React to identify specific elements in the array when they’re updated, removed, or added.
- What is a ref in React?
    - A reference to an DOM element
- What are Higher-Order-Components?
    - Higher-Order Components are custom components that wrap other components within them. They can dynamically accept one or more components as children without modifying or copying any of the children’s behavior. They allow for code reuse and state abstraction and manipulation.
- How to pass data to components?
    - Context
    - Props
- What is the difference between state and props?
    - State is read and write. It cause components to rerender and can be passed as a prop.
    - Prop is read only. It can be used as the initial value of a state or can be a setState function.
- What is a React Fragment
    - React fragments are a special feature in React that let you write group children elements or components without creating an actual node in the DOM.


### Hooks

- What are the useCallback & useMemo hooks used for?

#### useEffect

- What you return in useEffect runs before component unmount.


#### Misc

- `useWorker` allows multithreading in react

## SQL


### Joins

- Joins work as a venn diagram. The stuff in the middle is an inner join. The stuff in on either the left or right is a left/right join accordingly.
- 