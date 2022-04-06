## clientWidth
The Element.clientWidth property is zero for inline elements and elements with no CSS; otherwise, it's the inner width of an element in pixels. It includes padding but excludes borders, margins, and vertical scrollbars (if present).

When clientWidth is used on the root element (the \<html> element), (or on \<body> if the document is in quirks mode), the viewport's width (excluding any scrollbar) is returned. 
<img src="./images/dimensions-client.png">

## offsetWidth
The HTMLElement.offsetWidth read-only property returns the layout width of an element as an integer.

Typically, offsetWidth is a measurement in pixels of the element's CSS width, including any borders, padding, and vertical scrollbars (if rendered). It does not include the width of pseudo-elements such as ::before or ::after.

If the element is hidden (for example, by setting style.display on the element or one of its ancestors to "none"), then 0 is returned.

<img src="./images/dimensions-offset.png">

## scrollWidth
The Element.scrollWidth read-only property is a measurement of the width of an element's content, including content not visible on the screen due to overflow.

The scrollWidth value is equal to the minimum width the element would require in order to fit all the content in the viewport without using a horizontal scrollbar. The width is measured in the same way as clientWidth: it includes the element's padding, but not its border, margin or vertical scrollbar (if present). It can also include the width of pseudo-elements such as ::before or ::after. If the element's content can fit without a need for horizontal scrollbar, its scrollWidth is equal to clientWidth.

## <a href="https://developer.mozilla.org/en-US/docs/Web/API/Element/getBoundingClientRect">getBoundingClientRect</a>
The Element.getBoundingClientRect() method returns a DOMRect object providing information about the size of an element and its position relative to the viewport.
```html
domRect = element.getBoundingClientRect();
```
The returned value is a DOMRect object which is the smallest rectangle which contains the entire element, including its padding and border-width. The left, top, right, bottom, x, y, width, and height properties describe the position and size of the overall rectangle in pixels. Properties other than width and height are relative to the top-left of the viewport.
<img src="./images/element-box-diagram.png">
The width and height properties of the DOMRect object returned by the method include the padding and border-width, not only the content width/height. In the standard box model, this would be equal to the width or height property of the element + padding + border-width. But if box-sizing: border-box is set for the element this would be directly equal to its width or height.

The returned value can be thought of as the union of the rectangles returned by getClientRects() for the element, i.e., the CSS border-boxes associated with the element.

Empty border-boxes are completely ignored. If all the element's border-boxes are empty, then a rectangle is returned with a width and height of zero and where the top and left are the top-left of the border-box for the first CSS box (in content order) for the element.

The amount of scrolling that has been done of the viewport area (or any other scrollable element) is taken into account when computing the bounding rectangle. This means that the rectangle's boundary edges (top, right, bottom, left) change their values every time the scrolling position changes (because their values are relative to the viewport and not absolute).

If you need the bounding rectangle relative to the top-left corner of the document, just add the current scrolling position to the top and left properties (these can be obtained using window.scrollX and window.scrollY) to get a bounding rectangle which is independent from the current scrolling position.