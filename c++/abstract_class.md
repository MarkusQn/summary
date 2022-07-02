# Abstract classes
- *pure virtual function*: abstract function without implementation (Java: `abstract` methods)
- Syntax: signature followed by `= 0`
- Classes that contain at least one *pure virtual function* are known as *abstract base classes*.
- Abstract base classes cannot be instantiated.

Example:
```C++
class Polygon {
  public:
    virtual int area () =0;
};

class Rectangle: public Polygon {
  private:
    int width, height;
  public:
    Rectangle(int w, int h) : width(w), height(h) {}
    int area () { return (width * height); }
};

int main () {
  Rectangle rect {10, 5};
  Polygon* p = &rect;
  cout << p->area() << endl;
  return 0;
}
```