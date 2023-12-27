---
layout: default
title: Home
---

<p align="center">

<h2 style="font-family: 'Architects Daughter', 'Helvetica Neue', Helvetica, Arial, sans-serif;">
    <a href="https://sheraadams.github.io/#software-engineering-and-design">Software Engineering and Design</a>
</h2>

<h2 style="font-family: 'Architects Daughter', 'Helvetica Neue', Helvetica, Arial, sans-serif;">
    <a href="https://sheraadams.github.io/#data-structures-and-algorithms">Data Structures and Algorithms</a>
</h2>

<h2 style="font-family: 'Architects Daughter', 'Helvetica Neue', Helvetica, Arial, sans-serif;">
    <a href="https://sheraadams.github.io/#databases">Databases</a>
</h2>

<h2 style="font-family: 'Architects Daughter', 'Helvetica Neue', Helvetica, Arial, sans-serif;">
    <a href="https://sheraadams.github.io/#professional-assessment">Professional Assessment</a>
</h2>

<h2 style="font-family: 'Architects Daughter', 'Helvetica Neue', Helvetica, Arial, sans-serif;">
    <a href="https://sheraadams.github.io/code">Code Review</a>
</h2>

</p>



# Capstone Presentation
- For my [Software Engineering and Design](https://sheraadams.github.io/#software-engineering-and-design) enhancement, I added a pie chart and a bar chart that describe age upon outcome by category and outcome type of the Grazioso Salvare client database. Here are my [enhancements](https://sheraadams.github.io/#software-engineering-and-design-enhancments).

- For my [Data Structures and Algorithms](https://sheraadams.github.io/#data-structures-and-algorithms) enhancement, I increased the efficiency of the CS250 Java slideshow application by using an ArrayList in place of conditional branching to control the slideshow view. Here are my [enhancements](https://sheraadams.github.io/#data-structures-enhancements).

- For my [Databases](https://sheraadams.github.io/#databases) enhancement, plan to set up the database and dashboard locally (on both Mac and Windows), outlining this process to improve future workflows. Additionally, I plan to implement a field mask to hide confidential fields such as client names from the dashboard data table. Here are my [enhancements](https://sheraadams.github.io/#database-enhancements).
  
# Software Engineering and Design

## About the Project

For my software engineering enhancement, I chose to focus on the [CS340 Grazioso Salvare interactive dashboard](https://www.youtube.com/watch?v=ZxHuFK2Ne_o). The artifacts for this project include the zipped folder that includes the Python, Jupyter Notebook, and PNG Grazioso logo. The client dashboard employs the Model-View-Controller (MVC) design pattern, using PyMongo for CRUD functions. The architecture includes a MongoDB NoSQL database and Python code for communication. The dashboard is programmed using [MongoDB](https://www.mongodb.com/products/platform/cloud) and [Python](https://python.org/), and it uses [Jupyter Notebook](https://jupyter.org/) and [Dash](https://plotly.com/) to create interactive graphs. The RESTful protocol enhances HTTP and provides a scalable, adaptable, and easy-to-maintain structure. The client dashboard is designed to provide functionality and a user-friendly interface for interacting with a database using creation, updating, reading, reading, and deletion database management functions that utilize the PyMongo software. 

<div align="center">
  <p><strong>CS340 Client Server Development Dashboard</strong></p>
  <img src="https://sheraadams.github.io/assets/img/top.jpeg" width="800" alt="CS340 Client Server Developmemt Dashboard: d1">
</div>

## Software Engineering Artifacts
The artifacts for this category include the zipped CS340 Folder including the Python, Jupyter Notebook files, and the Grazioso PNG logo.


## A review of the client's functional requirements: 

- The application should provide an interface for clients to interact with the Grazioso database.
- The application should allow lookup by common profiles.
- The application should have:
  - Interactive options to filter the data
  - A data table that dynamically responds to filter options
  - A geolocation chart that displays the animal’s coordinates
  - An additional chart that dynamically responds to the filter options

## Code Review: Python read function

The Python file gives CRUD helper functions for working with our database. The **read()** function takes in a query as a parameter and will try to use the built-in pyMongo function, find(). If the query is found, the function will return the query, if it is not found the function will print an error and return an empty list.

```python
# Create method to implement the R in CRUD.
    def read(self, query):
        #try to read the data, if success return query
        try:
            results = list(self.collection.find(query))
            return results
        # error reading the data, print "error" and return empty list
        except Exception as e:
            print(f"Error reading documents: {e}")
            return []

```

## Code Review: The Jupyter Notebook file

In the following code, we log in to the database with our credentials and create a data frame from all records. We remove the _id column from the data frame and create an instance of the JupyterDash class.
```python
db = CRUD(username, password)

df = pd.DataFrame.from_records(db.read({}))
df.drop(columns=['_id'],inplace=True)

app = JupyterDash(__name__)
```

The app.layout section creates the layout of the app using HTML code. In our layout, we create a dash table to display the database columns and rows.
```python
    # Format the data table 
    dash_table.DataTable(
        id='datatable-id',
        columns=[{"name": i, "id": i, "deletable": False, "selectable": True} for i in df.columns],
        style_data_conditional=[{'if': {'column_editable': False},'backgroundColor': 'white','color': 'rgb(30, 30, 30)'}],
        style_header_conditional=[{'if': {'column_editable': False},'backgroundColor': 'white','color': 'rgb(30, 30, 30)'}],
        data=df.to_dict('records'),
        editable=False,
        filter_action="native",
        sort_action="native",
        sort_mode="multi",
        column_selectable=False,
        row_selectable="single",
        row_deletable=False,
        selected_columns=[],
        selected_rows=[0],
        derived_virtual_selected_rows=[],
        page_action="native",
        page_current=0,
        page_size=10,
       # derived_virtual_data=df.to_dict('records'),
        style_header={'border': '1px solid pink'},
    ),
```

With the **update dashboard()** function we can update the dashboard according to the selected filter type. We have an input callback that takes the filter as a parameter and we have output callbacks for the data and columns of the data table.
```python
@app.callback(Output('datatable-id', 'data'),
              Output('datatable-id', 'columns'),
              [Input('filter-type', 'value')])
def update_dashboard(filterValue, **kwargs):
    # Filter data based on the selected type 
    if filterValue == 'mountain':
        # save the df as result of the read function call passing the mountain query as a parameter
        df = pd.DataFrame.from_records(db.read(mountain_rescue_query))
    elif filterValue == 'water':
        # save the df as result of the read function call passing the water query as a parameter
        df = pd.DataFrame.from_records(db.read(water_rescue_query))
    elif filterValue == 'disaster':
        # save the df as result of the read function call passing the disaster query as a parameter
        df = pd.DataFrame.from_records(db.read(disaster_query))
    else:
        # return all data if reset (default datatable/ read all data)
        df = pd.DataFrame.from_records(db.read({'animal_type': {'$in': ["Dog", "Cat", "Bird", "Other"]}}))
    
    # delete the _id collumn
    df.drop(columns=['_id'],inplace=True)   
    # define the column properties
    columns = [{"name": i, "id": i, "deletable": False, "selectable": True} for i in df.columns]
    # create a dictionary from the data frame
    data = df.to_dict('records')
    #return a tuple of data, columns
    return (data, columns)
```
When we run the Jupyter Notebook file, we can see the interactive data table, geolocation map, and chart display and interactively respond to the user selection. We can filter the selection with the radio buttons labeled “Water Rescue”, “Mountain Rescue”, “Disaster Rescue”, or “Reset”.

## Software Engineering and Design Enhancements

For my enhancement, I would like to add two new charts that describe additional characteristics of the Grazioso client database like animal age upon outcome and animal outcome type. The additional charts should describe new characteristics of the data, giving the end user a more holistic understanding of the animal shelter data.  As the dashboard currently employs a scatter chart to describe the breed distribution of the animals, other characteristics such as outcome type and age upon outcome could be described by bar and pie charts respectively. 

My enhancement aligns with outcome 2, developing professional, technically sound communications that are appropriately adapted to specific audiences and contexts. With this enhancement in mind, I considered the audience and asked myself how I could better facilitate the need for thorough, meaningful, and descriptive data visualizations to be utilized by Grazioso Salvare and their client base. By adding additional graphs that describe other important characteristics of our animal shelter database set, we can provide the end user with more well-rounded data from multiple categories. While some clients may be concerned only with the breed distribution of the pets, many clients may wish to understand additional characteristics such as outcome and age upon outcome to make more informed decisions. 

My enhancement also aligns with outcome 1, employing strategies for building collaborative environments that enable diverse audiences to support organizational decision-making. Providing the user with multifaceted insights can facilitate informed decisions in computer science and business. The interactive dashboard allows the end user to interact through filter selection and search and visualize descriptive charts of the data depending on the selection. My enhancements also facilitate a collaborative environment in which many users from diverse backgrounds and technical experience can explore and understand data effectively through visualizations and graphs, ultimately supporting informed organizational decision-making.

## Enhancement Summary: 
- Add a bar chart that describes outcome type by count.
- Add a pie chart that describes age upon outcome by count.


## Enhancement Part 1 Psuedocode for bar (outcome type)
SET datatable-id derived_virtual_data to input callback
SET filter-type to input callback
SET bar-id to output callback
**def update_bar(viewData, filterValue, **kwargs)**
DEFINE dataframe as the derived_virtual_data
IF outcome_type exists in the dataframe
	COUNT the members of each category and store the result in a variable
	RENAME the columns for the dataframe
	DEFINE a pie chart with labels and values based on the counted members 
	RETURN the bar chart
ELSE 
	RETURN an empty chart

## Flowchart for age upon outcome chart categories

<div align="center">
  <p><strong>Flowchart for Age Upon Outcome</strong></p>
  <img src="https://sheraadams.github.io/assets/img/swe_flow.jpg" width="400" alt="CS 340 Enhancement">
</div>

## Enhancement Part 2 Pseudocode for pie (age upon outcome) chart
SET datatable-id derived_virtual_data to input callback
SET filter-type to input callback
SET pie-id to output callback
**def update_pie(viewData, filterValue, **kwargs)**
DEFINE dataframe as the derived_virtual_data
IF age_upon_outcome_in_weeks exists in the dataframe
	DEFINE categories for 0, 4, 12, 26, 52, 100, 200, 500, infinity weeks
	DEFINE a label for each category
	CREATE a column called ‘age_group’ to store the categories
	COUNT the members of each category and store the result in a variable
	RENAME the columns for the dataframe
	DEFINE a pie chart with labels and values based on the counted members 
	RETURN the pie chart
ELSE 
	RETURN an empty chart

## Additional Insights

As we can see below, we have more insights that we can bring to the dataset beyond just the breed of the animals. Without overwhelming the user with all of the charts shown below, we can choose the visualizations that deliver the most value to the client. Grazioso Salvare’s potential clients may be particularly interested in animal age by outcome and outcome type. 

As we can see in the chart below, there are too many age categories shown for animal age by outcome type and we may simplify this for the user by creating 6-10 distinct age categories. 


<div align="center">
  <p><strong>More Insights From this Dataset</strong></p>
  <img src="https://sheraadams.github.io/assets/img/tableau.jpeg" width="600" alt="CS 340 Additional Insights">
</div>

See the [Tableau data here](https://public.tableau.com/app/profile/sheraadamsmedia/viz/AACoutcomes/Dashboard1?publish=yes).

## High-Fidelity Wireframe for my enhancement
<div align="center">
  <p><strong>Wireframe Enhancement Proposal</strong></p>
  <img src="https://sheraadams.github.io/assets/img/wireframe.jpeg" width="600" alt="CS 340 Enhancement">
</div>

Note: colors and shapes in this wireframe may vary in implementation and should look more similar to the colors shown in the existing scatter chart above. 

## Course objectives

**Course Outcome 1.** Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision-making in the field of computer science.

In this project, I developed a dashboard that allows the end user to interact through filter selection and search and visualize descriptive charts of the data depending on the selection. This enhancement facilitates a collaborative environment in which many users from diverse backgrounds and technical experience can explore and understand data effectively, ultimately supporting informed organizational decision-making.

**Course Outcome 2.** Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts.

In this project, I considered the audience at each step asking myself how I could facilitate the need for thorough, meaningful, and descriptive data visualizations. By adding additional graphs that describe other important characteristics of our animal shelter database set, we can provide the end user with more well-rounded data. Providing the user with multifaceted insights can facilitate informed decision-making.

# Data Structures and Algorithms

## About the Project 

For my data structures and algorithms enhancement, I would like to make changes to the Java slideshow that I created for CS250 Software Development Lifecycle. The artifact for this project includes the Java code and Eclipse project as well as a runnable JAR file that we created in this class as an easy-to-distribute and share compact artifact. 

The Java program is a slideshow console application that uses Swing and JFrame to create a GUI window. JFrame serves as a container for the application window. The program utilizes HTML for styling the text and embedding the images in the panels including a slide pane, a text pane, and a button pane. This program uses the Model-View-Controller (MVC) design pattern where the images and text are the model, the Java code is the application logic and the buttons allow the client to interact with the software. 


<div align="center">
  <p><strong>CS 250 Slide Show</strong></p>
  <img src="https://sheraadams.github.io/assets/img/slideshow.jpeg" width="800" alt="CS 250 Slideshow d1">
</div>

(Southern New Hampshire University, n.d.)

## Database Artifacts
The artifacts for this category include the zipped CS340 Folder including the Python files and the Grazioso PNG logo.

## A review of the client's functional requirements

 - The application should have an ordered list of destinations from the most popular location to the fifth most popular.
 - Each destination on the list should have the following attributes shown:
   - Destination name
   - Destination short description (one sentence)
   - Destination picture
   - Destination link
   
## Data Structures Artifacts
The Eclipse Project folder is called SlideShow or Slide Show Enhanced and the SlideShow.jar or SlideShowE.jar.   

## The Code Review

The initComponent() method is used to define each of the components, set display properties like font, color, and size, and set listeners for the buttons. 

```java
  private void initComponent() {
        this.card = new CardLayout();
        this.cardText = new CardLayout();
        this.slidePane = new JPanel();
        this.textPane = new JPanel();
        this.textPane.setBackground(Color.WHITE);
        this.textPane.setBounds(5, 470, 790, 50);
        this.textPane.setVisible(true);
        this.buttonPane = new JPanel();
        this.btnPrev = new JButton();
        this.btnNext = new JButton();
        this.lblSlide = new JLabel();
        this.lblTextArea = new JLabel();
        this.setSize(800, 600);
        this.setLocationRelativeTo((Component)null);
        this.setTitle("Top Detox Destinations");
        this.getContentPane().setLayout(new BorderLayout(10, 50));
        this.setDefaultCloseOperation(3);
        this.slidePane.setLayout(this.card);
        this.textPane.setLayout(this.cardText);
//...
```
We can see that this application uses a conditional statement based on the value of the index “i”. Based on the numerical value of i, the string is reassigned to the corresponding string. The string itself is HTML code that formats text or formats and loads an image and lblSlide.setText() function is responsible for updating the slide.

```java
        for(int i = 1; i <= 5; ++i) {
            this.lblSlide = new JLabel();
            this.lblTextArea = new JLabel();
            this.lblSlide.setText(this.getResizeIcon(i));
            this.lblTextArea.setText(this.getTextDescription(i));
            this.slidePane.add(this.lblSlide, "card" + i);
            this.textPane.add(this.lblTextArea, "cardText" + i);
        }
//...
    private String getResizeIcon(int i) {
        String image = "";
        if (i == 1) {
            image = "<html><body><img width= '800' height='500' src='" + this.getClass().getResource("/resources/costarica.jpg") + "'</body></html>";
        } else if (i == 2) {
            image = "<html><body><img width= '800' height='500' src='" + this.getClass().getResource("/resources/sedona.jpg") + "'</body></html>";
        } else if (i == 3) {
            image = "<html><body><img width= '800' height='500' src='" + this.getClass().getResource("/resources/nepal.jpg") + "'</body></html>";
        } else if (i == 4) {
            image = "<html><body><img width= '800' height='500' src='" + this.getClass().getResource("/resources/egypt.jpg") + "'</body></html>";
        } else if (i == 5) {
            image = "<html><body><img width= '800' height='500' src='" + this.getClass().getResource("/resources/grandcanyon.jpg") + "'</body></html>";
        }

        return image;
    }
// ...
```

We can increase the efficiency of our application using a data structure in place of conditional branching. When considering a data structure for our application we are most concerned about access. Insertions into the user’s top five destination list should is not expected to be a frequent task. Once per-day insertions and rearranging would likely be sufficient.

## Data Structures Enhancements
For this enhancement, plan to align the project to course outcome number 3 and solve an algorithmic problem using computer science practices and standards to implement a solution. In doing this, I will manage the trade-offs involved in design choices. Specifically, for this application, I would like to increase the efficiency of the CS250 Java slideshow application by using the ArrayList structure in place of conditional branching to control the slideshow view.

In the analysis of the algorithms available to this application, I will compare some of the common structures that could be considered. Hash tables and binary search trees have higher overhead costs and require storage space for the structure itself. Hash tables are best for small data sets in which fast searches are a priority. Hash tables (or Java HashMap), however, do not preserve order. The binary search tree is for cases when data sets are likely to grow, and fast searches are important. Binary search trees require maintenance to keep them balanced, so this is a consideration.

<div align="center">
  <p><strong>Big O Cheatsheet (Eric Drowell, n.d.)</strong></p>
  <img src="https://sheraadams.github.io/assets/img/bigo.jpeg" width="600" alt="Big O Cheatsheet">
</div>  

Java’s ArrayList is good for fast random access to elements by index, and it preserves the order of elements. In terms of access, the array structure performs very well and has the average run-time space complexity of O(1) to O(N), which is linear (with O(N) being the worst case, in which N is the number of elements in the array). The ArrayList offers advantages in terms of pure runtime and space complexity when frequent insertions and sorting are not needed. If dynamic insertions and deletions are to be expected at runtime, the resulting run-time space complexity would be O(N). For our specific use case of managing a top-five favorites list where sorting is unnecessary, the space complexity remains O(N) due to the straightforward nature of the list. If sorting were required, the expected run-time space complexity could range from O(N) to O(N log N) if using mergesort. 

In choosing a structure for this application, we must consider the context and intended use of the application as well as the resources available and the expected scale for its use. I considered both the ArrayList and the linked list for this application as both of these structures offer the benefits of order preservation and fast access. Ultimately, I decided that the linked list brings additional complexity and overhead storage for the structure itself when this is not necessary for daily insertions and sorting. It is always important to consider the needs of the end-user and the context of the application carefully before choosing an appropriate structure. Additionally, it is always crucial to weigh the trade-offs associated with data structure selection to avoid excessive development and revisions.  

As our application is small now, our improved data structure may not noticeably increase the efficiency of the application, however, if the top five list were to grow, or if the number of users accessing their top five would scale largely, the dependence on a solid data structure would become increasingly impactful. Adopting an appropriate data structure improves the adaptability, reusability, and scalability of this application and helps us to conform to software engineering best practices (course outcome 3).

## Flowchart for the Slideshow
Note: the flowchart for this application does not change with the new algorithm implementation. 

<div align="center">
  <p><strong>Flowchart for the Slideshow</strong></p>
  <img src="https://sheraadams.github.io/assets/img/slide_flow.jpeg" width="400" alt="Slide Show Flowchart">
</div>  

## Course outcomes

**Course Outcome 1:** Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision-making in the field of computer science.

In my work for this project, my team practiced communication in an Agile environment in which inclusion and iterative development are the expectation. For this project, initially, we were tasked with building a travel website in which the user’s Top Five Destinations” would be shown as well as their description, and a hyperlink to the location package. As the project evolved and changed over time, however, the focus shifted from all destinations to “Detox Destinations”. 

Suddenly, it became clear how important iterative development is in software development as elements would need to be changed before the end of the sprint. When the time came, the changes were simple to implement as a result of my adherence to software engineering best practices that produce modular, adaptable code that follows industry standard naming conventions.

**Course Outcome 2:** Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts.

I considered the target audience and the context at every point of this application’s development and as a result, the software received perfect marks upon submission.  

**Course Outcome 3:** Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices.

I implemented an algorithmic solution that was appropriate for this software in its intended context. The ArrayList is a flexible, lightweight, dynamic structure well suited to the task of primary access and occasional, insertion, sorting, and deleting elements. 

# Databases
For my database enhancement, I chose to focus on the client-server database created for Grazioso Salvare to help identify potential animals for training. This artifact includes the Python and Jupyter files created for CS340 along with a png Grazioso Salvare logo. 
I have several recommendations for this project to better align to software engineering and security best practices which I will outline and briefly describe. 

The first recommendation that I have aligns with software security best practices (outcome 5). To ensure enhanced security in this application, I recommend removing all deprecated imports from this application. Deprecated imports pose a security risk as they refer to functions or libraries that are no longer supported. In this case, the deprecated JupyterDash library is no longer supported and it has been replaced by the Dash library. To benefit from ongoing bug fixes and to ensure compatibility going forward, it is recommended to access the Dash library and its methods only.

The second recommendation that I have aligns with software security best practices and software engineering best practices utilizing well-founded tools (outcomes 5). The recommendation is to remove all hard-coded passwords from the Python files and add exception handling to inform the user if the password is incorrect or empty. To remove all passwords from the file, we must first set an environment variable. We can set the environment variable within our code and run the code once before removing it. In this same session, using the Visual Studio code terminal, we can export the database password and run the Jupyter Notebook file. After this initial setup, our password is saved as an environment variable and it can be accessed as long as we remain in the same terminal session.

The third recommendation that I have aligns with utilizing well-founded tools to align with software engineering best practices (outcome 4). For this recommendation, I suggest adding exception handling to inform the user if the password is incorrect or empty. To do this, we should add try and except statements to the CRUD.py init function. Doing this will allow more graceful termination and will notify the user if the password is incorrect rather than providing the user with errors that result from the empty data frame. Doing this will also prevent unnecessary code processing when there is no data. 

The fourth recommendation that I have for this dashboard is that a field mask be added to hide confidential client names. This recommendation aligns with developing professional visual communications that are appropriately adapted to specific audiences and contexts (course outcome 2). In the case of Grazioso Salvare’s client dashboard, we know that many of the outcomes include pets that have been adopted, transferred, returned to their owner, or deceased among other outcome types. As some of the pets belong to private owners who may not wish for their pet’s private name to be publicly displayed, a field mask could be used to hide the confidential names of pets that are no longer available for training from new, unrelated clients that do not need to know these pets personal identifying information. Implementing these changes to the dashboard can allow Grazioso Salvare to adhere to industry regulations that require the confidentiality of private client data. 

My final enhancement is an outline of the process to reproduce the dashboard locally on both Windows and Mac operating platforms.  This enhancement reduces future workflows and increases efficiency. While the setup process was generally similar, there are important differences in these workflows as you will observe in the documentation below. This enhancement aligns with course outcome 4, using well-founded and innovative techniques, skills, and tools in computing practices to implement computer solutions that deliver value and accomplish industry-specific goals. 
 
Enhancements Summary:
 - Remove deprecated imports
 - Align password handling to industry standards by removing all hard-coded passwords from the Python files
 - Align password handling to industry standards by adding exception handling in the case that the password is incorrect.
 - Add a field mask to hide confidential client names.
 - Outline the reproduction process for both Mac and Windows Operating Platforms

## Enhancement Part 1
Remove deprecated imports
Recommended changes to ensure security and compatibility:
Remove the first line: “from jupyter_dash import JupyterDash” as this line is not necessary.
Update the JupyterDash instance app = JupyterDash(__name__) to app = Dash(__name__).

## Enhancement Part 2
Remove all hard-coded passwords from the main.py Python file as follows in pseudocode:
SET environment variable DB_PASS to the password
DEFINE username
GET the environment password and save it as the password
IF the password is not empty
	CREATE an instance of the CRUD class to interact with the database
ELSE 
	DISPLAY “Database password is not set.”
	EXIT 

## Enhancement Part 3
Add exception handling in the case that the password is not correct. See the following pseudocode as an example:
def __init__(self, USER, PASS):      
	SET host
	SET username
	SET database name
	SET the collection name
	TRY:
		SET client to the connection string
		SET database
		SET collection 
		DISPLAY “connection successful”
	CATCH the exception
		DISPLAY “incorrect password”
		EXIT

## Enhancement Part 4
Add a field mask to hide confidential fields from the database. See the following pseudocode as an example:

```python
Def mask_field(name):
	RETURN ‘******’
```

## Enhancement Part 5
### Windows Installations 
To set up the database and dashboard application locally we will need to install the [Windows Subsystem for Linux](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/), the [Mongo Shell](https://www.mongodb.com/try/download/shell) and [MongoDB Compass](https://www.mongodb.com/try/download/compass).

### Mac Installations
 To set up the database and dashboard application locally we will need to install [MongoDB Compass](https://www.mongodb.com/try/download/compass) and [Homebrew](https://brew.sh). We will also install the MongoDB community using the terminal and the homebrew package manager:

Bash:
```bash
brew tap mongodb/brew
brew install mongodb-community
brew services start mongodb-community
```

Similarly, we can stop the MongoDB service when we are finished with our work in a testing environment with: 

Bash:
```bash
brew services stop mongodb-community
```

## Instructions (All Platforms)
After completing the previous installation process depending on your operating system, the following instructions will walk you through importing AAC data into MongoDB, creating a user, and connecting to the database using the Linux shell. To begin working with this software on Windows OS, first follow these instructions to install the bash shell. Otherwise, when working with the environment provided on the Apporto virtual lab, proceed with the following: 

### 1. Import the AAC data

To import AAC data into MongoDB, you can use the `mongoimport` command as follows replacing the correct username and password for your use.

```bash
# in the linux shell run the following command to import the aac_shelter_outcomes excel document
mongoimport --username="${MONGO_USER}" --password="${MONGO_PASS}" --port=${MONGO_PORT} --host=${MONGO_HOST} --type=csv --headerline --db AAC --collection animals --authenticationDatabase admin --drop /usr/local/datasets/aac_shelter_outcomes.csv
```

### 2. Create the user
Bash:
```bash
use admin;
db.createUser({
  user: "username",
  pwd: "password",
  roles: [
    { role: "readWrite", db: "AAC" }
  ]
});
```

### 3. Set the environment variables
Bash:
```bash
# set the environment
# determine the port number for Python connection settings 
printenv | grep -i mongo
# login the user
MONGO_USER=username
MONGO_PASS=password

```

### 4. Verify connection
Mongo shell:
```mongosh
# open the mongo shell
mongosh
// verify access to the database
show dbs
use AAC
// verify the database has the animals collection
show collections
// verify the collection has the csv document imported successfully 
db.animals.findOne()
// demonstrate a connection to the database using the logged-in user
db.runCommand({connectionStatus:1})
```

### 5. Add indexes to our database 

To increase data retrieval speed and our database's overall efficiency, we will add indexes for searches that we expect will be frequently used. We will add indexes for the breed and outcome type. 

Mongo shell:
```mongosh
db.animals.createIndex({ breed: 1 })
db.animals.createIndex({ breed: 1, outcome_type: 1 })
// verify the successful creation with simple queries: 
db.animals.find({ breed: "beagle" }).explain("executionStats")
db.animals.find({ breed: "beagle", outcome_type: "Transfer" }).explain("executionStats")
```

### 6. Install packages

Bash:
```bash
pip install dash==2.8.1
pip install dash-leaflet==0.1.9
pip install pandas==1.4.2
pip install plotly
pip install jupyter-dash
pip install numpy
pip install matplotlib
pip install pymongo
```

### 7. Run the Jupyer Notebook file

You can easily run the Jupyter Notebook file in [Visual Studio Code](https://code.visualstudio.com/download) using the latest Python language extension along with the latest Jupyter Notebook and Python extensions. 

## Course Outcomes

**Course Outcome 4:** Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices to implement computer solutions that deliver value and accomplish industry-specific goals.
By developing this application locally on both Windows and Mac I used industry best practice and used industry best practices to ensure performance and compatability in diverse computing environments.

**Course Outcome 5:** Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources.

Giving only the designated user access to read and write to the AAC database prevents unauthorized users from accessing and modifying the database. Additionally stopping the MongoDB service when we are finished frees up resources on the system when the service is no longer being used. 

Further, removing all hard-coded passwords and instead setting and retrieving database passwords from the environment allows our project to conform to secure software best practices and reduce vulnerabilities that hard-coded configurations can allow. 

## Database Enhancements

I reproduced this project locally with a step-by-step guide detailing the process. This enhancement reduces future workflows and increases efficiency. While the setup process was generally similar, there are important differences in these workflows.

To conform to secure software best practices I removed the hard-coded passwords from the Jupyter Notebook file and used environment variables for all passwords in the program. To accomplish this within the project, I set the environment variables in the terminal in Visual Studio Code. 

Hard coding passwords should always be avoided and sensitive information should be protected and stored safely. Configuration settings like passwords should always be separated from code to prevent accidental mishandling and unauthorized access. 

In addition to these enhancements, I added a character mask to hide confidential fields in the case that a client name should be confidential for some uses.

Check out my [references](https://sheradams.github.io/references.md) here.

<div style="text-align: center;">
  <p><strong>Proudly crafted with ❤️ by <a href="https://github.com/sheraadams" target="_blank">Shera Adams</a>.</strong></p>
</div>

