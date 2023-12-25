---
layout: default
title: Home
---

# Professional Assessment 

Lorem ipsum dolor sit amet, in qui paulo semper interpretaris, mazim nostrud ornatus vis cu, sed ne constituto ullamcorper. Ius errem omittam honestatis no. Vel ne primis delectus petentium, sed alienum efficiendi et. Quo vulputate maiestatis ne, iudico dissentias at usu, an eam iudicabit liberavisse.

Cum melius tractatos accusamus no, ea assum honestatis vix. Usu eirmod volumus persecuti te. Wisi recusabo et vix, ut est quod euripidis. Sed sale paulo exerci eu, voluptua repudiare ea his. Similique definitiones sed ad, quo modus volumus percipit ei. Has te probatus salutatus, eu eos soluta vulputate.

Ut praesent democritum vix, verterem assentior comprehensam has id. Nullam erroribus ea sit. Duo propriae laboramus concludaturque ad, ex sit invidunt efficiantur ullamcorper. His vero animal complectitur ne, nonumes reprehendunt per id. Quo ceteros indoctum petentium cu. Te erat singulis nam, idque legere te sed. Ei qui salutatus reprimique temporibus, accusamus definitionem ad sea, ne usu ullum labore senserit.

**Course Outcome 1:** Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision-making in the field of computer science.

**Course Outcome 2:** Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts.

**Course Outcome 3:** Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices.

**Course Outcome 4:** Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals.

**Course Outcome 5:** Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources.


# Capstone Presentation
- For my [Software Engineering and Design](https://sheraadams.github.io/#software-engineering-and-design) enhancement, I added a pie chart and a bar chart that describe age upon outcome by category and outcome type of the Grazioso Salvare client database. Here are my [enhancements](https://sheraadams.github.io/#software-engineering-and-design-enhancments).

- For my [Data Structures and Algorithms](https://sheraadams.github.io/#data-structures-and-algorithms) enhancement, I increased the efficiency of the CS250 Java slideshow application by using an arraylist in place of conditional branching to control the slideshow view. Here are my [enhancemens](https://sheraadams.github.io/#data-structures-enhancements).

- For my [Databases](https://sheraadams.github.io/#databases) enhancement, plan to set up the database and dashboard locally (on both Mac and Windows), outlining this process to improve future workflows. Additionally I plan to implement a field mask to hide confidential fields such as client name from the dashboard data table. Here are my [enhancements](https://sheraadams.github.io/#database-enhancements).
  
# Software Engineering and Design

## About the Project

For my sofware engineering enhancement, I chose to focus on the [CS340 Grazioso Salvare interactive dashboard](https://www.youtube.com/watch?v=ZxHuFK2Ne_o). The artifacts for this project include the zipped folder that includes the Python, Jupyter Notebook, and PNG Grazioso logo. The client dashboard employs the Model-View-Controller (MVC) design pattern, using PyMongo for CRUD functions. The architecture includes a MongoDB NoSQL database and Python code for communication. The dashboard is programmed using [MongoDB](https://www.mongodb.com/products/platform/cloud) and [Python](https://python.org/), and it uses [Jupyter Notebook](https://jupyter.org/) and [Dash](https://plotly.com/) to create interactive graphs. The RESTful protocol enhances HTTP and provides a scalable, adaptable, and easy-to-maintain structure. The client dashboard is designed to provide functionality and a user-friendly interface for interacting with a database using creation, updating, reading, reading, and deletion database management functions that utilize the PyMongo software. 

<div align="center">
  <p><strong>CS340 Client Server Development Dashboard</strong></p>
  <img src="https://sheraadams.github.io/assets/img/top.jpeg" width="800" alt="CS340 Client Server Developmemt Dashboard: d1">
</div>

## Software Engineering Artifacts
The artifacts for this categort include the zipped CS340 Folder including the Python, Jupyter Notebook files, and the Grazioso PNG logo.


## Dashboard Code Review

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

In the following code, we log in to the database with our credentials and create a data frame from all records. We remove the _id column from the data frame and create an instance of the JupyterDash class.
```python
db = CRUD(username, password)

df = pd.DataFrame.from_records(db.read({}))
df.drop(columns=['_id'],inplace=True)

app = JupyterDash(__name__)
```

The app.layout section creates the layout of the app using HTML code. In our layout we create a dash table to display the database columns and rows.
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

## Software Engineering and Design Enhancements

As we can see below, we have more insights that we can bring to the dataset beyond just the breed of the animals. Without overwhelming the user with all of the charts shown below, we can choose the visualizations that deliver the most value to the client. Grazioso Salvare’s potential clients may be particularly interested in animal age by outcome and outcome type. 

As we can see in the chart below, there are too many age categories shown for animal age by outcome type and we may simplify this for the user by creating 6-10 distinct age categories. 


<div align="center">
  <p><strong>More Insighs From this Dataset</strong></p>
  <img src="https://sheraadams.github.io/assets/img/tableau.jpeg" width="800" alt="CS 340 Additional Insights">
</div>

See the [Tableau data here](https://public.tableau.com/app/profile/sheraadamsmedia/viz/AACoutcomes/Dashboard1?publish=yes).

## High-Fidelity Wireframe for my enhancement
<div align="center">
  <p><strong>Wireframe Enhancement Proposal</strong></p>
  <img src="https://sheraadams.github.io/assets/img/wireframe.jpeg" width="800" alt="CS 340 Enhancement">
</div>

Note: colors and shapes in this wireframe may vary in implementation and should look more similar to the colors shown in the existing scatter chart above. 

## Software Engineering Outcomes

Lorem ipsum dolor sit amet, in qui paulo semper interpretaris, mazim nostrud ornatus vis cu, sed ne constituto ullamcorper. Ius errem omittam honestatis no. Vel ne primis delectus petentium, sed alienum efficiendi et. Quo vulputate maiestatis ne, iudico dissentias at usu, an eam iudicabit liberavisse.

Cum melius tractatos accusamus no, ea assum honestatis vix. Usu eirmod volumus persecuti te. Wisi recusabo et vix, ut est quod euripidis. Sed sale paulo exerci eu, voluptua repudiare ea his. Similique definitiones sed ad, quo modus volumus percipit ei. Has te probatus salutatus, eu eos soluta vulputate.

Ut praesent democritum vix, verterem assentior comprehensam has id. Nullam erroribus ea sit. Duo propriae laboramus concludaturque ad, ex sit invidunt efficiantur ullamcorper. His vero animal complectitur ne, nonumes reprehendunt per id. Quo ceteros indoctum petentium cu. Te erat singulis nam, idque legere te sed. Ei qui salutatus reprimique temporibus, accusamus definitionem ad sea, ne usu ullum labore senserit.

# Data Structures and Algorithms

For my data structures and algorithms enhancement, I would like to make changes to the Java slideshow that I created for CS250 Software Development Lifecycle. The artifact for this project includes the Java code and Eclipse project as well as a runnable JAR file that we created in this class as an easy-to-distribute and share compact artifact. 

The Java program is a slideshow console application that uses Swing and JFrame to create a GUI window. JFrame serves as a container for the application window. The program utilizes HTML for styling the text and embedding the images in the panels including a slide pane, a text pane, and a button pane. This program uses the Model-View-Controller (MVC) design pattern where the images and text are the model, the Java code is the application logic and the buttons allow the client to interact with the software. 


<div align="center">
  <p><strong>CS 250 Slide Show</strong></p>
  <img src="https://sheraadams.github.io/assets/img/slideshow.jpeg" width="800" alt="CS 250 Slideshow d1">
</div>

(Southern New Hampshire University, n.d.)

## Database Artifacts
The artifacts for this categort include the zipped CS340 Folder including the Python files and the Grazioso PNG logo.
   
## Data Structures Artifacts
The Eclipse Project folder is called SlideShow or Slide Show Enhanced and the SlideShow.jar or SlideShowE.jar.   

## Slideshow Code Review

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
We can see that this application uses a conditional statement based on the value of the index “i”. Based on the numerical value of i, the string is reassigned to corresponding string. The string itself is HTML code that formats text or formats and loads an image and lblSlide.setText() function is responsible for updating the slide.

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

Lorem ipsum dolor sit amet, in qui paulo semper interpretaris, mazim nostrud ornatus vis cu, sed ne constituto ullamcorper. Ius errem omittam honestatis no. Vel ne primis delectus petentium, sed alienum efficiendi et. Quo vulputate maiestatis ne, iudico dissentias at usu, an eam iudicabit liberavisse.

Cum melius tractatos accusamus no, ea assum honestatis vix. Usu eirmod volumus persecuti te. Wisi recusabo et vix, ut est quod euripidis. Sed sale paulo exerci eu, voluptua repudiare ea his. Similique definitiones sed ad, quo modus volumus percipit ei. Has te probatus salutatus, eu eos soluta vulputate.

Ut praesent democritum vix, verterem assentior comprehensam has id. Nullam erroribus ea sit. Duo propriae laboramus concludaturque ad, ex sit invidunt efficiantur ullamcorper. His vero animal complectitur ne, nonumes reprehendunt per id. Quo ceteros indoctum petentium cu. Te erat singulis nam, idque legere te sed. Ei qui salutatus reprimique temporibus, accusamus definitionem ad sea, ne usu ullum labore senserit.

## Flowchart for the Slideshow
Note: the flowchart for this application does not change with the new algorithm implementation. 

<div align="center">
  <p><strong>Flowchart for the Slideshow</strong></p>
  <img src="https://sheraadams.github.io/assets/img/slide_flow.jpeg" width="500" alt="Slide Show Flowchart">
</div>  

## Data Structures Outcomes
Lorem ipsum dolor sit amet, in qui paulo semper interpretaris, mazim nostrud ornatus vis cu, sed ne constituto ullamcorper. Ius errem omittam honestatis no. Vel ne primis delectus petentium, sed alienum efficiendi et. Quo vulputate maiestatis ne, iudico dissentias at usu, an eam iudicabit liberavisse.

Cum melius tractatos accusamus no, ea assum honestatis vix. Usu eirmod volumus persecuti te. Wisi recusabo et vix, ut est quod euripidis. Sed sale paulo exerci eu, voluptua repudiare ea his. Similique definitiones sed ad, quo modus volumus percipit ei. Has te probatus salutatus, eu eos soluta vulputate.

Ut praesent democritum vix, verterem assentior comprehensam has id. Nullam erroribus ea sit. Duo propriae laboramus concludaturque ad, ex sit invidunt efficiantur ullamcorper. His vero animal complectitur ne, nonumes reprehendunt per id. Quo ceteros indoctum petentium cu. Te erat singulis nam, idque legere te sed. Ei qui salutatus reprimique temporibus, accusamus definitionem ad sea, ne usu ullum labore senserit.


# Databases
For my database enhancement, I chose to focus on the client-server database created for Grazioso Salvare to help identify potential animals for training. This artifact includes the Python and Jupyter files (only Python files are recommended for the final artifact. For more information about this see recommendation #3) created for CS340 along with a png Grazioso Salvare logo. 

## Database Enhancements
I have several recommendations for this project to better align to software engineering and security best practices which I will outline:

Enhancements Summary:
 - Remove deprecated imports
 - Align password handling to industry standards by removing all hard-coded passwords from the Python files
 - Align password handling to industry standards by adding exception handling in the case that the password is incorrect.
 - Add a field mask to hide confidential client names.
 - Outline the reproduction process for both Mac and Windows Operating Platforms

## Flowchart for password enhancement

<div align="center">
  <p><strong>Flowchart for Password Enhancement</strong></p>
  <img src="https://sheraadams.github.io/assets/img/db_flow.jpg" width="800" alt="CS 340 Enhancement">
</div>


## Database Outcomes
Lorem ipsum dolor sit amet, in qui paulo semper interpretaris, mazim nostrud ornatus vis cu, sed ne constituto ullamcorper. Ius errem omittam honestatis no. Vel ne primis delectus petentium, sed alienum efficiendi et. Quo vulputate maiestatis ne, iudico dissentias at usu, an eam iudicabit liberavisse.

Cum melius tractatos accusamus no, ea assum honestatis vix. Usu eirmod volumus persecuti te. Wisi recusabo et vix, ut est quod euripidis. Sed sale paulo exerci eu, voluptua repudiare ea his. Similique definitiones sed ad, quo modus volumus percipit ei. Has te probatus salutatus, eu eos soluta vulputate.

Ut praesent democritum vix, verterem assentior comprehensam has id. Nullam erroribus ea sit. Duo propriae laboramus concludaturque ad, ex sit invidunt efficiantur ullamcorper. His vero animal complectitur ne, nonumes reprehendunt per id. Quo ceteros indoctum petentium cu. Te erat singulis nam, idque legere te sed. Ei qui salutatus reprimique temporibus, accusamus definitionem ad sea, ne usu ullum labore senserit.


Check out my [references](https://sheradams.github.io/references.md) here.

<div style="text-align: center;">
  <p><strong>Proudly crafted with ❤️ by <a href="https://github.com/sheraadams" target="_blank">Shera Adams</a>.</strong></p>
</div>
