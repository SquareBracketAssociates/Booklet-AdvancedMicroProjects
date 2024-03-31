## Microdown miniprojects
@cha:microdown

Microdown is a markup language compatible with a subset of markdown. 
It is used by the Pharo community to produce slides, booklets, and documentation. 
Microdown heavily uses Visitors. 
The repository is at 

```
https://github.com/pillar-markup/microdown
```

### Blog and its posts

A nice little project is to use Microdown to define a blog and its posts.
A potential roadmap is the following:

- Given a file repository we should generate a little table of contents. For this, we can reuse the HTML generation of Microdown. To do so we can do it either by generating a microdown document using the microdown builder and passing it to the HTML visitor. Or by creating the tree of objects for the table of contents and applying the HTML generation on it. 
- You can also render all the post to generate HTML files. 
- Finally having a visitor that extract the title of a post and a couple of line of the first paragraph so that the user can see a summary before clicking to get access to the full post can be nice. 


### Link checker

In Microdown, the writer can refer to figures and anchors as well as to web site as shown here after.

```
## A Section 
@anchor1

![A caption](figures/fig.png label=figanchor)

[ Pharo web site ](https://pharo.org)
https://pharo.org

In Section *@anchor1@* we can find Fig. *@figanchor@*.
```

We would like to have a checker that reports to the users the set of references (defined using the `*@xxx@*` instruction  that are not found. 


### Table of contents

We would like to have a table of content builder. Given a book, the Toc builder will generate a microdown document tree containing references to the corresponding book entities (chapter, section)

### Book Sanitizer

When writing documents, we often have some writing guidelines. 

#### Guideline sample
Here are some guidelines about writing style and spelling

- Write "backend", not "back-end" or "back end".
- Write "subpresenter", not "sub-presenter".
- Methods without comment have an empty line after the method selector.
- Methods do not have a period on the last line.
- Write "Pharo image", not "Pharo Image.
- Do not use protocol references because they are not useful and may change.
- Write "Section 6.1", not "section 6.1".
- Write "Figure 6.2", not "figure 6.2".
- Caption should start with an uppercase and terminate by a period.
- Titles (section, chapter, ...) should just have the first letter capitalized.
```
### The great book.
```
- Figure caption should end with a period and be capitalized.
```
![The great figure.]()
```
- Class names should be surrounded by `
- Only use tab for code indentation
- For paragraphs terminate the label with a period
```
#### Cap. 
```

#### Job

A book sanitizer can perform modifications of the document tree to reflect them. 
A subsequent version could change the files to reflect such change so that the user can
save them.

A sanitizer should be configurable to take into account book guidelines.



### Automatic Numbering 

When writing a book users do not want to be forced to write in the exact same level of nesting than the template interpretation. For example, in this book # is to represent a LaTeX part, and ## for a chapter. However, it would possible to simply change the numbering so that a writer can write # for title and to use meta data at the level of the file to control this. 

```
{  "nesting":0 }
```

could mean that # is for a chapter title, ## a section, ### a paragraph

Conversely 

```
{  "nesting":1 }
```
could mean that ## is for a chapter title, ### a section,  


### Rendered math downloader

To render math in non latex mode, the microdown renderer in Pharo performs a request to an online service. A cool feature is to change the logic to do change the logic so that 


- After each request to the server, save the gif or png representing the render math expression with a unique name in the ressources folder of the current file directory. A possible name is to take two letters of path elements plus a counter. So the 3 expressions in foo/bar/ will be named foba3.png

- [optional] Change the math code to reflect that the corresponding rendered expression is available 

``` 
$$
    \frac{1}{2}
$$

```

into 

``` 
$$ % renderedAs=foba3.png
    \frac{1}{2}
$$

```

- Modify the system so that the request is only performed if there is no ressources for the given expression. When the ressources is found, it should use the corresponding rendered result graphic object.

#### Better contents encoding

Note that computing the name based on the order of appareance in the text is not really robust to change. If the user inserts a new math expression this will invalidate the pre existing renderer. Propose a better system based on the expression contents for example the hash of a zip. 




