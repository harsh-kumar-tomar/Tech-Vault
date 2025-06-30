Canvas is a powerful drawing tool in [[Android]] that allows developers to create custom graphics, render text, and draw shapes directly onto a `View` or `Bitmap`. It is a part of the `android.graphics` package and is widely used for custom view implementations, game development, and complex UI rendering.

## Imp Classes

### Canvas class 
to directly draw on bitmap or view 
- `drawColor(int color)`: Fills the canvas with a specified color.
- `drawRect(Rect rect, Paint paint)`: Draws a rectangle.
- `drawCircle(float cx, float cy, float radius, Paint paint)`: Draws a circle.
- `drawText(String text, float x, float y, Paint paint)`: Draws text.
- `drawBitmap(Bitmap bitmap, float left, float top, Paint paint)`: Draws a bitmap.
### Paint class
Defines the style and color attributes for the shapes and text drawn on the Canvas
- `setColor(int color)`: Sets the color.
- `setStyle(Paint.Style style)`: Sets the style (e.g., `FILL`, `STROKE`).
- `setStrokeWidth(float width)`: Sets the stroke width.
- `setTextSize(float textSize)`: Sets the text size.

two different ways to implement custom view  :

1. Combine different Views: such as TextView, ImageView, and Drawable resources.  
2. Custom View: draw it yourself using the canvas and math.