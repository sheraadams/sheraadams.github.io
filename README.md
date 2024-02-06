<p align="center">
  <h2 style="font-family: 'Architects Daughter', 'Helvetica Neue', Helvetica, Arial, sans-serif;">
        <a href="https://sheraadams.github.io">ePortfolio</a><br>
      <a href="https://sheraadams.github.io/#professional-assessment">Professional Assessment</a><br>
      <a href="https://sheraadams.github.io/#code-review">Code Review</a><br>
      <a href="https://sheraadams.github.io/#software-engineering-and-design">Software Engineering and Design</a><br>
      <a href="https://sheraadams.github.io/#data-structures-and-algorithms">Data Structures and Algorithms</a><br>
      <a href="https://sheraadams.github.io/#databases">Databases</a><br>
  </h2>
</p>

## Professional Assessment 

## ePortfolio Overview

- For my [Software Engineering and Design](https://sheraadams.github.io/#software-engineering-and-design) enhancement, I added Freetype and IrrKlang libraries to my OpenGL C++ project, adding sound to the scene, and rendering user-friendly instructions and x,y, and z coordinates of a target development object to the screen. Find my [Software Engineering and Design artifacts here](https://sheraadams.github.io/#software-engineering-and-design-artifacts).

- For my [Data Structures and Algorithms](https://sheraadams.github.io/#data-structures-and-algorithms) enhancement, I increased the adaptability and maintainability of the CS250 Java slideshow application by using an ArrayList in place of conditional branching to control the slideshow view. Having an efficient data structure in place will be particularly important as the application scales. Find my [Data Structures and Algorithms artifacts here](https://sheraadams.github.io/#data-structures-and-algorithms-artifacts).

- For my [Database](https://sheraadams.github.io/#databases) category enhancement, I set up the database and dashboard locally, and I added two additional charts that describe age upon outcome and outcome type attributes from the Grazioso dataset. I enhanced the security of the project by removing all hard-coded passwords and adding password handling. **Finally, I updated libraries to the newest supported versions.** I also implemented a field mask to hide confidential fields such as client names from the dashboard data table. Find my [Database artifacts here](https://sheraadams.github.io/#databases-artifacts).

## Code Review

A code review is an organized analysis of one’s code in the context of the software development community for teaching, testing, and analyzing the code base. Code reviews are a static test that we can perform for our code, and they are a way that we can test the quality of our code while ensuring completeness and adherence to the client’s requirements. Code reviews are an important practice in computer science as they allow us to think critically about our work while allowing outside parties to contribute to and examine our code. Promoting collaboration, code reviews allow us to improve our code by inviting others to share their feedback about our work. 

I conducted an informal code review for this course, reviewing projects from three prior courses to analyze the strengths and weaknesses in my code, and proposing enhancements covering software engineering, data structures and algorithms, and databases categories. My enhancements were selected to highlight my proficiency in [all five course outcomes](https://sheraadams.github.io/outcomes). Here is the code review on YouTube:

<p align="center">
  <a href="https://youtu.be/RqVvmqJ1A3s">
    <img src="https://sheraadams.github.io/assets/img/preview.jpg" alt="CS499 Code Review">
  </a>
</p>

## Software Engineering and Design

For my software engineering enhancement, I enhanced the OpenGL final project created for CS330 Computational Graphics in the Winter Term of 2023. The artifacts for this project include the zipped folder with the C++ code, Visual Studio solution, and the file dependencies and libraries required to run the project on the Windows operating system in Visual Studio 2022. I selected this artifact because it showcases my skill in crafting engaging user experiences and my drive to challenge myself to learn new things. In CS330, added custom key controls to enable the user to interact with the scene and I added key controls to scroll, move, and scale a target object with a key press on the x, y, and z axes. I added a vector of textures that could be accessed through an index variable and scrolled on an object with a key press. *I enhanced my OpenGL project by adding the IrrKlang 3D sound library to add music to the scene. I also implemented the FreeType library, rendering text over the scene that displays the key control options and the real-time x, y, and z coordinates of the target object as it is manipulated by the user.* Through my enhancements, I met course outcomes 1, 2, and 4: 

**Course Outcome 1. Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision-making in the field of computer science.**

For my enhancement, I rendered text to the screen to indicate the real-time coordinates and sizes of the target object as it is manipulated by the user with a key press on the x, y, and z axes. My development control enhancement reduces workflows and increases precision and accuracy in the design process. My enhancement also enables the developer to create more realistic replications that are accurate in scale and design and to simulate the implications of physics more accurately and efficiently. 

- **My enhancement met course outcome 1, employing strategies for building collaborative environments that enable diverse audiences to support organizational decision-making through skills in C++, graphics programming, OpenGL, and software engineering.** 

**Course Outcome 2. Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts.**

I met outcome 2, delivering professional quality communications, by adding sound and text to the OpenGL application. Rendering the instructions and the x, y, and z coordinates and sizes allows the user to engage with the interactivity controls in a practical way and increases the user’s confidence and understanding of the application. Adding sound and key-press sound controls for the user also increased the scene interactivity while placing the user in control of the audio experience. 

- **Utilizing skills in OpenGL, C++, sound engineering, and Visual Studio, I delivered professional quality communications through adding sound and sound controls to the application to meet the need for control and interactivity in the context of professional quality software solutions.**  

**Course Outcome 4. Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals (software engineering/design/database).**

I met outcome 4 as I demonstrated skills using well-founded tools and innovative techniques for the purpose of implementing computer solutions that accomplish industry-specific goals by adding sound and text to my scene to engage the user and increasing the interactivity. I used the Irrklang sound library to add music to the application, and I added the FreeType library to add text over the scene. Adding sound, text, and development controls transforms our simpler OpenGL project to a more interactive application that engages the user through text, and sound mediums in addition to the scene itself. 

- **In my enhancement, I demonstrated an ability to use well-founded and innovative techniques, skills, and tools to implement computer solutions that deliver value and accomplish industry-specific goals using skills in OpenGL, C++, game development, and Microsoft Visual Studio.**

### Challenges and Lessons Learned
As I worked on my project, I learned to become more familiar with the FreeType and IrrKlang libraries. I learned to work with functions like IrrKlang’s setSoundVolume() and play2D() and I learned to use IrrKlang’s drop() function to clean up after the render loop. Though I originally did not plan to manipulate sound with a key press, in the end, I decided this would be a necessary feature to ensure that the end user is in control of the audio experience. I added user control (keys 1 and 2) to turn up or down the volume, and I set the volume to begin at 20% on program launch. 

I did not face any significant challenges with the implementation of the libraries, but any time we introduce new libraries into our Visual Studio projects, the configuration of libraries and dependencies is often a large part of our work. In my work, I learned to be familiar with the locations of the new dependencies for the additional libraries as well as their nuances. My largest challenge was limiting the overall file size while considering compatibility and accessibility for the end user. In my work, I found that some of the greatest reductions in file size could be accomplished by simply converting PNG images to JPEG. I also found that testing on multiple machines and multiple IDEs helped me to improve the quality of my code, assess constraints, and optimize my Visual Studio configurations with the user in mind.

<div align="center">
  <p><strong>Software Engineering and Design Enhancement</strong></p>
  <img src="https://sheraadams.github.io/assets/img/SWE_en.jpeg" width="800" alt="Software Engineering and Design Enhancement">
</div>

### Software Engineering and Design Artifacts
The artifacts for this category include the zipped folder including the C++ and .h files, and the file dependencies needed to run the project in Microsoft Visual Studio. Please feel free to contact me for a copy of the enhanced artifact.  

## Data Structures and Algorithms

For my data structures and algorithms category, I enhanced the Java Swing slideshow that I developed as a part of CS250 Software Development Lifecycle. The artifact for this project includes the Java Eclipse project and code and the executable JAR file in the zipped folder. The slideshow is a desktop application that uses Swing and JFrame to create a GUI window where JFrame serves as a container for the application window. The program utilizes HTML for styling the text and formatting images in the panels. This program uses the Model-View-Controller (MVC) design pattern where the images and text are the model, the Java code is the application logic, and the buttons allow the client to interact with the software. For CS250, the Java slideshow application was meant to be a starting point and an early iteration of the larger vacation booking system project. *I enhanced the slideshow wireframe application by increasing the adaptability, maintainability, and resource efficiency of the code by using an efficient data structure to replace the if-else conditional branching currently controlling the view of the slideshow.* Through this enhancement, I demonstrated proficiency in course outcome 3:

**Course Outcome 3. Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices (data structures and algorithms).**

Before enhancement, the slideshow operated on a conditional statement that defined the contents of 10 JLabels that were created for each user based on the value of the index variable.  I improved the resource and memory usage of the application by changing this hard-to-maintain conditional statement to an appropriate data structure and ensured that with each slide, only two JLabels were created and subsequently clearing and adding the contents to the panes according to the value the index. My enhancement improved the adaptability, reusability, and scalability of this application by conforming to software engineering best practices. 

Though our wireframe slideshow application data started out small and our improved data structure may not noticeably increase the run-time efficiency of the application (the current run-time cost to create the GUI contents for one user is 35 and it is 11n with the ArrayList – see below for the cost analysis), as the application scales and the logic is adopted by the larger application, several issues would arise. If the number of users accessing their top five would scale largely, the dependence on a solid data structure would become increasingly impactful in terms of memory, performance, and code maintenance. With the ArrayList, the average runtime space complexity is still linear and it is comparable to the conditional branching in place (before enhancement, the run time space complexity was 0(1)) and after, it is expected to be O(1) to O(N) with the added benefit of better resource management and better maintainability). Further, as we are most concerned about access, the ArrayList runtime space complexity for access would be O(1), which is the same. 

Overall, Java’s ArrayList is good for fast random access to elements by index, it has linear average run-time space complexity, and it preserves the order of elements. In terms of access, when sorting and insertion are not a primary need, the ArrayList structure performs very well. My enhancement Increased the code maintainability and resource efficiency of the application by implementing an appropriate data structure. 

- **In my work, I met outcome 3, evaluating solutions that solve a given problem using algorithmic principles and computer science practices using computer science, documentation, algorithm analysis, Java programming, and HTML programming.**

<div align="center">
  <p><strong>Algorithm Analysis</strong></p>
  <img src="https://sheraadams.github.io/assets/img/analysis.jpg" width="800" alt="Algorithm Analysis">
</div>

### Challenges and Lessons Learned

In the completion of this enhancement, I learned to be more holistic in my approach when considering an appropriate data structure for this application. I learned to consider the context, the intended use, resources available, and the expected scale of the application first when considering a data structure as run time efficiency alone is not usually enough information. I initially considered the ArrayList, the Binary Search Tree, and the Linked List for this application as each of these structures offer the benefits of order preservation and fast access. Ultimately, I decided that the Linked List and Binary Search Tree bring additional overhead storage requirements that may not be reasonable for daily insertions and sorting with a primary use of access alone. Quantifying algorithmic differences (especially when they are relatively small) can be challenging at times, however, I found an algorithmic analysis exercise as shown below to be a helpful tool for comparing the space complexity before and after enhancement. 

In the end, I learned that it is always important to consider the needs of the end-user and the context of the application carefully first before choosing an appropriate structure. Additionally, it is always crucial to weigh the trade-offs associated with a data structure. Doing so can prevent unnecessary revision, cost, and maintenance.

<div align="center">
  <p><strong>Java Slide Show</strong></p>
  <img src="https://sheraadams.github.io/assets/img/slideshow.jpeg" width="800" alt="Java Slide Show">
</div>

### Data Structures and Algorithms Artifacts
The artifact for this project includes a zipped folder with the .jar executable and the Eclipse Java project.

  - You can find the [original artifact](https://github.com/sheraadams/sheraadams.github.io/blob/main/artifacts/DSA_Example.zip) here.  
  - You can find the [enhanced artifact](https://github.com/sheraadams/sheraadams.github.io/blob/main/artifacts/DSA_Enhanced.zip) here.  

## Databases

For my database enhancement, I enhanced the PyMongo Dashboard created for CS340 Client Server Development in the Fall of 2023. The artifacts for this project include the zipped folder that includes the Python, Jupyter Notebook, and PNG Grazioso logo. The client dashboard was developed for Grazioso Salvare to help identify potential animals for training and it employs the Model-View-Controller (MVC) design pattern.  The architecture includes a MongoDB NoSQL database and Python code for interaction with the database through CRUD (Create, Read, Update, Delete) functions. The interactive dashboard relies on Dash, dash-leaflet, numpy, and matplotlib libraries. The RESTful protocol enhances HTTP and provides a scalable, adaptable, and easy-to-maintain structure. The application previously included a data table that displayed the contents of the database, a scatter chart showing the distribution of breeds, and a geolocation chart showing the latitude and longitude of the selection. *For my enhancement, I added two additional graphs to describe other features of the dataset, a name mask to hide confidential names from the client’s view, resource deallocation, password handling, and I updated all libraries to their newest supported versions.* I met course outcomes 1, 2, 4, and 5 with my enhancements:

**Course Outcome 1. Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision-making in the field of computer science.**

In my enhancement, I added pie and bar charts to show age upon outcome and outcome type to give the user a more holistic understanding of the animal shelter data. Providing the user with multifaceted insights facilitates informed decisions in computer science and business using data. The charts that I included, like the previously included scatter chart, are interactive and they dynamically respond to the filter selection. My enhancement facilitates a collaborative environment in which users from diverse backgrounds and technical experience can explore and understand data effectively through visualizations regardless of their experience with NoSQL database itself that informs the graphs. 

- **My enhancement demonstrates my proficiency in enabling diverse audiences to support informed organizational decision-making through software development skills in Python, databases, NoSQL, MongoDB, and data analysis.**

**Course Outcome 2. Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts.**

For my enhancement, I also added a field mask to hide confidential client names. In the case of Grazioso Salvare’s client dashboard, we know that many of the outcome types include pets that have been adopted, transferred, returned to their owner, or deceased among other outcomes. As some of the pets belong to private owners who may not wish for their pet’s private name to be publicly displayed, I implemented a field mask to hide the confidential names of all pets from the clients' view as the client does not need to know the pet’s identifying information. Adding this change to the dashboard can allow Grazioso Salvare to adhere to industry regulations that require the confidentiality of private client data. 

- **My enhancement demonstrates mastery of developing professional communications that are technically sound and adapted to specific audiences and contexts through software development skills in Python programming, databases, and software security.**

**Course Outcome 4. Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals (software engineering/design/database).**

Using well-founded tools and practices to align with software engineering best practices, I added exception handling to inform the user if the password is incorrect or empty. I accomplished this by adding try and except statements to the CRUD.py init() function. Doing this allows more graceful termination and notifies the user if the password is incorrect rather than providing the user with errors that result from failed attempts to load the data frame. My solution accomplishes the specific goal of informing the user if credentials are incorrect and preventing the unnecessary execution of code in the case of failed login attempts. 

- **My enhancement demonstrates my ability use well-founded and innovative techniques in computing to implement solutions that deliver value and accomplish industry-specific goals using skills in software security, software engineering, Python programming, and databases.**

**Course Outcome 5. Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources.**

**Aligning with software security best practices, I removed the deprecated imports from this application and updated libraries to the newest versions.** According to the Plotly GitHub repository, for versions of Dash greater than or equal to 2.11, Jupyter support is now built-in, meaning that the previously supported Jupyter_Dash library is now obsolete (Plotly, n.d.). Deprecated imports pose a security risk as they do not benefit from bug fixes and security updates as newer and supported methods do. To address this issue, I updated all instances of the JupyterDash methods to Dash methods. Additionally, I removed all hard-coded passwords and instead set environment variables in the terminal session in Visual Studio Code. Anticipating adversarial exploits in software, my enhancement mitigates some of the risks associated with software development and ensures the security of data using software engineering best practices. 

- **My enhancement demonstrates a security mindset that anticipates adversarial exploits in software architecture, mitigates design flaws, and ensures privacy and security of data through skills in software security, software engineering, Python programming, Visual Studio Code, and Jupyter Notebook.**

<div align="center">
  <p><strong>Database Enhancement Flowchart</strong></p>
  <img src="https://sheraadams.github.io/assets/img/db_flow.jpg" width="600" alt="Database Enhancement Flowchart">
</div>

### Challenges and Lessons Learned

In the completion of these enhancements, I learned several things. First, I learned to be comfortable setting and retrieving environment variables within Jupyter Notebook files in Visual Studio Code. Also in this process, I faced a minor challenge when testing my local setup on both Mac OS and Windows. As I tested my enhanced dashboard application on multiple devices, I noticed that I had errors on one of the machines, and no errors on the other after updating my app instance from JupyterDash to Dash. With a little investigation, I discovered the cause of the error an outdated Dash library on the problem machine. With Dash libraries older than 2.11, the code will not successfully create the dashboard and JupyterDash would still be required. I was able to resolve the issue by updating the Dash library to the newest version on both machines to finally reproduce the dashboard locally on both machines successfully. My work in this project taught me importance of researching and verifying each of the dependencies used in our code in all circumstances. This project was a valuable experience for me and it increased my confidence working with databases and with Python. 

<div align="center">
  <p><strong>Grazioso Client Server Dashboard</strong></p>
  <img src="https://sheraadams.github.io/assets/img/DB_en.jpeg" width="800" alt="Grazioso Client Server Dashboard">
</div>

### Databases Artifacts
The artifacts for this category include the zipped folder including the Python, Jupyter Notebook files, and the Grazioso PNG logo.

  - You can find the [original artifact](https://github.com/sheraadams/sheraadams.github.io/blob/main/artifacts/Database_Example.zip) here.  
  - You can find the [enhanced artifact](https://github.com/sheraadams/sheraadams.github.io/blob/main/artifacts/Database_Enhanced.zip) here.

## References

Big-O Algorithm Complexity Cheat Sheet (Know Thy Complexities!) @ericdrowell. (n.d.). 
https://www.bigocheatsheet.com/

Detlefsen, A., & Manico, J. (2015). Iron-Clad Java: Building Secure Web Applications (1st ed.). McGraw-
Hill Education. ISBN: 978-0-07-183589-3.

Google. (2023). Google UX Design Professional Certificate. Coursera. https://www.coursera.org/
professional-certificates/conception-ux-google

Plotly. (n.d.). GitHub - plotly/jupyter-dash: OBSOLETE - Dash v2.11+ has Jupyter support built in! GitHub. 
https://github.com/plotly/jupyter-dash

SPK and Associates. (2022, July 10). Software Engineering Best Practices: Code Reviews – Part 1. SPK And 
Associates. https://www.spkaa.com/blog/software-engineering-best-practices-code-reviews-
part-1

Check out my [artifact multimedia references](https://sheraadams.github.io/references) here.

<div style="text-align: center;">
  <p><strong>Proudly crafted with ❤️ by <a href="https://github.com/sheraadams" target="_blank">Shera Adams</a>.</strong></p>
</div>

