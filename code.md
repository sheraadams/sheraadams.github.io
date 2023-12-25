---
layout: default
title: Home
---

# Code Review

Lorem ipsum dolor sit amet, in qui paulo semper interpretaris, mazim nostrud ornatus vis cu, sed ne constituto ullamcorper. Ius errem omittam honestatis no. Vel ne primis delectus petentium, sed alienum efficiendi et. Quo vulputate maiestatis ne, iudico dissentias at usu, an eam iudicabit liberavisse.

Cum melius tractatos accusamus no, ea assum honestatis vix. Usu eirmod volumus persecuti te. Wisi recusabo et vix, ut est quod euripidis. Sed sale paulo exerci eu, voluptua repudiare ea his. Similique definitiones sed ad, quo modus volumus percipit ei. Has te probatus salutatus, eu eos soluta vulputate.

Ut praesent democritum vix, verterem assentior comprehensam has id. Nullam erroribus ea sit. Duo propriae laboramus concludaturque ad, ex sit invidunt efficiantur ullamcorper. His vero animal complectitur ne, nonumes reprehendunt per id. Quo ceteros indoctum petentium cu. Te erat singulis nam, idque legere te sed. Ei qui salutatus reprimique temporibus, accusamus definitionem ad sea, ne usu ullum labore senserit.

- See my [Software Engineering and Design and Databases categories](https://sheraadams.github.io/#dashboard-code-review) here.

- See my [Data Structures and Algorithms](https://sheraadams.github.io/#slideshow-code-review) here.

## Dashboard Code Review

The Python CRUD.py file gives CRUD helper functions for working with our database. The **read()** function takes in a query as a parameter and will try to use the built-in pyMongo function, find(). If the query is found, the function will return the query, if it is not found the function will print an error and return an empty list.

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

With the **update dashboard()** function we can update the dashboard according to the selected filter type. We have an input callback that takes the filter filterValue as a parameter and we have output callbacks for the data and columns of the data table.
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

# Slideshow Code Review
The initComponent() method is used to define each of the components, set display properties like font, color, and size, and set listeners for the buttons. 

```java
    private void initComponent() {
        // create the card layout components
        this.card = new CardLayout();
        this.cardText = new CardLayout();
       
        // add the jpanel container for the slides    
        this.slidePane = new JPanel();
        this.textPane = new JPanel();
      
        // set the position of the text box   
        this.textPane.setBackground(Color.WHITE);
      
        // set the location of the text box
        this.textPane.setBounds(5, 470, 790, 50);
        this.textPane.setVisible(true);
       
        // create a button pane and buttons
        this.buttonPane = new JPanel();
        this.btnPrev = new JButton();
        this.btnNext = new JButton();

        // create the slide area and the text area    
        this.lblSlide = new JLabel();
        this.lblTextArea = new JLabel();

        // set the size of the gui    
        this.setSize(800, 600);
        this.setLocationRelativeTo((Component)null);
        
        // set the title of the window
        this.setTitle("Top Detox Destinations");

        // add horizontal and vertical padding
        this.getContentPane().setLayout(new BorderLayout(10, 50));
        this.setDefaultCloseOperation(3);
        
        // set the layout to the pane
        this.slidePane.setLayout(this.card);
        this.textPane.setLayout(this.cardText);
//...
```
We can see that this application uses a conditional statement based on the value of the index “i”. Based on the numerical value of i, the string is reassigned to corresponding string. The string itself is HTML code that formats text or formats and loads an image and lblSlide.setText() function is responsible for updating the slide.

```java
        // set the image and text to the value assigned by the condition 
        //for the matching value of i
        for(int i = 1; i <= 5; ++i) {
            // create a new jlabel each time
            this.lblSlide = new JLabel();
            this.lblTextArea = new JLabel();
            // set the text to html string contents at the position of i 
            this.lblSlide.setText(this.getResizeIcon(i));
            // set the text to the html string contents at the position of i
            this.lblTextArea.setText(this.getTextDescription(i));
            // add the contents to the pane
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

We can increase the efficiency of our application using a data structure in place of conditional branching by creating an ArrayList to store the HTML code. 

```java
    // create the string arraylist that stores the image html code that loads the images
    private ArrayList<String> createImages()  {
    	ArrayList<String> slideImages = new ArrayList<>();
        slideImages.add("<html><body><img width= '800' height='500' src='" + 
        this.getClass().getResource("/resources/costarica.jpg") + "'</body></html>");
        slideImages.add("<html><body><img width= '800' height='500' src='" + 
        this.getClass().getResource("/resources/sedona.jpg") + "'</body></html>");
        slideImages.add("<html><body><img width= '800' height='500' src='" + 
        this.getClass().getResource("/resources/nepal.jpg") + "'</body></html>");
        slideImages.add("<html><body><img width= '800' height='500' src='" + 
        this.getClass().getResource("/resources/egypt.jpg") + "'</body></html>");
        slideImages.add("<html><body><img width= '800' height='500' src='" + 
        this.getClass().getResource("/resources/grandcanyon.jpg") + "'</body></html>");
        return slideImages;
    }
```

We call the following function initially and whenever the user presses the 'next' or 'previous' buttons to update the pane with the images and text. 

```java

    private void showSlide() {
        // clear the pane first
        this.slidePane.removeAll();
        this.textPane.removeAll();

        // create the jlabel if it doesn't exist
        if (this.lblSlide == null) {
            this.lblSlide = new JLabel();
            this.lblTextArea = new JLabel();
        }

        // get the current slide contents from the arraylists
        this.lblSlide.setText(this.slideImages.get(currentSlideIndex));
        this.lblTextArea.setText(this.slideText.get(currentSlideIndex));

        // add the contents to the pane
        this.slidePane.add(this.lblSlide, "card" + currentSlideIndex);
        this.textPane.add(this.lblTextArea, "cardText" + currentSlideIndex);

        // update the panes 
        this.slidePane.repaint();
        this.textPane.repaint();
    }
```

Using an appropriate data structure makes our program more efficient and it improves the adaptability, scalability and reusability of the program while conforming to software engineering best practices. 

Check out my [references](https://sheradams.github.io/references.md) here.

<div style="text-align: center;">
  <p><strong>Proudly crafted with ❤️ by <a href="https://github.com/sheraadams" target="_blank">Shera Adams</a>.</strong></p>
</div>

