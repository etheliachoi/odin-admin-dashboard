# Odin Project - Intermediate HTML and CSS: Admin Dashboard
## Description
This is the second and final project for the Intermediate HTML and CSS course. We are given a project design file and the goal is to recreate the page using grid. 

## Process
The first thing I did was look at the overall page design and think of how to use grid to lay things out. I decided to split up the sections into sidebar, header, and main content. After that, I handled each section one at a time by adding more elements into the HTML and styling them using more grids.

Each section also uses more grid to layout the elements. 

### Sidebar
I made the dashboard title a flexbox, the top menu bar as a grid parent, as well as the bottom menu bar. With this approach, I can easily make the icons align with the text, control the gaps between logo and text, and place the top and bottom menus at a distance from each other while reusing the same CSS.

### Header
I made the header element a grid with two rows, where the search bar is the top and the welcome message is the bottom row. Then, each row is also a grid parent for easier styling. I chose this approach instead of directly splitting the header grid into smaller chunks because it will be difficult to align the elements nicely in columns. I also avoided using flexbox even though the row is 1D, because I find it difficult to add extra space between certain elements without using padding, e.g. between the user's full name and buttons. Whereas for grid, I can simply add an empty column and adjust its width to solve this issue.

### Main Content
The main content is made into a grid parent with three sections: Projects, Announcements, and Trending where the latter two each have half the height of the project section. 

#### Projects
The project section is also made into a grid to place the six cards.  Initially, my thought was to add the icons on the cards using the pseudoelement `::after` to avoid duplicate HTML <img> tags. The pseudoelement allowed me to add all elements but since they are all in one line of CSS under `content`, they stacked up into a column by default and I was not able to style them into a row. At last, I had to make the six cards as grids to place the three icons on the bottom right.

#### Announcements
Initially, I made the card into a grid with three rows. Then, to add the line between the paragraphs, I realized using `border-bottom` on the grid item does not turn out nicely. For some reason, the border is at the bottom of the text, but not the bottom of the grid item where I want it. To solve this, I added two extra rows for where I need the line to be and styled them to take up minimal space. Then, I added a `border-top` to the empty grid item.

#### Trending
The card is a grid with four rows to place each user's information, which is also a grid of two columns to align the profile pic and texts. Then, each user's text box is a grid of two rows. This approach is rather redundant and can be improved by the solution mentioned in (4).

## Challenges
**(1)** Unable to make all the sections fit in one page without having to scroll down. I expect that by adding rules about height like `height: 100vh;` to the page container and specifying the grid template with fr, the grid will only take up the available space and not keep expanding downwards. 

**Solution**: remains unsolved.

**(2)** Announcements and Trending are half of height of Project, but the cards do not end on the same level, i.e. the last row of Project cards end way above the last row of Trending. This leads to a lot of empty grey space in the bottom of main content. 

**Solution**: For the overall layout, instead of using `grid-template-rows: 1fr 1fr;`, use `grid-template-rows: 1fr min-content;` so that the main content section adjusts its height according to the content.

**(3)** I wanted the paragraphs in Announcements to shrink into `text-overflow: ellipsis` style when the viewport shrinks, but could not get it to work at all.

**Solution**: I ended up opting to use `line-clamp` to restrict the number of lines shown so that the rest of the paragraph becomes ... as I wanted. This approach worked amazing! But the downside is it is not responsive.

**(4)** When I used grid to style Trending, I could not make the user icon span across two rows and have the adjacent column be two separate rows of text. I used `grid-template-rows` and `grid-rows` for this. 

**Solution**: I had to do a similar styling for the lower heading, this time, I used `grid-template-areas` and `grid-area` instead. It worked like magic! I am still unsure why it did not work for `grid-template-rows`.

## What I learned
Through this project, I learned a lot from designing and thinking how to lay things out in HTML so that I can style them with less resistance with CSS. I also got more confident with the parent-child relationship, e.g. knowing where to apply `display: grid` so that the targetted element will become a grid, knowing when to use `justify-items` vs `justify-self`, getting more comfortable using responsive units like %, and thinking carefully about what to use to achieve the effect I want. 