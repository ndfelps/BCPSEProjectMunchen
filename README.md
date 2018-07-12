# BCPSEProject: THEME-833 Fix for Munchen Theme

The goal of this project is to fix THEME-833 for the Munchen theme. There is  a second repo for the Bedazzled theme, which is also referenced in THEME-833. In both of these themes, there is an issue with subcategory menus overlapping each other when they are moused over in situations where the category list takes up two lines or more.

This may be a fairly small issue and simple to fix, but it creates a poor user experience for any customers trying to shop on stores with large catalogs.

## Reproducing The Issue

  1. Apply Munchen to your store
  2. Create enough categories to have two rows of categories on your storefront
  3. Create subcategories for all of those categories for easy testing
  4. Hover over a category in the top row, and then attempt to hover over one of the subcategories that appear
  
  ### Expected Result
  
  You are able to click on one of the subcategories that appear
  
  ### Actual Result
  
  The inistial drop down menu you had disappears as soon as you attempt to mouse over it, and the text of the categories overlaps on the drop down menu.
  
## The Solution

The solution to this one is to set the z-index for these elements to auto, which will prevent the new on hover elements from re-stacking against other elements once they appear. This is a pretty simple matter of throwing the following code into the theme.css:

.PageMenu .sf-menu li {
  z-index:auto;
}

I applied this, and a brief comment on the code, in lines 277-281 of theme.css.

## Testing

Here is a pretty brief video of me testing this fix: https://www.youtube.com/watch?v=xZ3XcRTJj2I&feature=youtu.be

There's not a whole lot to test here as this is a fairly small and simple fix, but as far as I could find this does not impact any other functionality on the theme, and does resolve this issue.
