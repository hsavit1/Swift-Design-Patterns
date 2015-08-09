#### A discourse in design patterns. Based off the wonderful book _Pro-Swift-Design-Patterns_. Please go grab a copy

# Themes
- tightly coupled components are the antithesis of design patterns. Two components are tightly coupled when one depends on the inner workings of another, or, put another way, when you can make a change to one component without also updating the other.
- tbc..
- tbc..

======
======
======
======


# Creation Patterns
1. The Object Template Pattern
2. The Prototype Pattern
3. The Singleton Pattern
4. The Object Pool Pattern
5. Object Pool Variations
6. The Factory Method Pattern
7. Abstract Factory Pattern
8. The Builder Pattern 

# Structural Patterns
1. The Adapter Pattern
2. The Bridge Pattern
3. The Decorator Pattern
4. The Façade Pattern
5. The Flyweight Pattern
6. The Proxy Pattern

# Behavioral Patterns
1. The Chain of Responsibility Pattern
2. The Command Pattern
3. The Mediator Pattern
4. The Observer Pattern
5. The Memento Pattern
6. The Strategy Pattern
7. The Visitor Pattern

=====
=====
=====
=====

# Creational 

###The Object Template Pattern

####What
The object template pattern uses a class or struct as the specification for the data types and logic for a given data type. Objects are created using the template, and values for the data are set during initialization, either through the use of default values in the template or using values provided by the component to the class or struct initializer, also known as the constructor.
    
####Why
The object template pattern provides the foundation for grouping data values and the logic that manipulates them together, known as encapsulation. Encapsulation allows an object to present an API to its consumers while hiding the private implementation of that API. This helps prevent the tight coupling of components.
    
####How
The object template pattern uses a class or struct to define a template from which objects are created. When an application component requires an object, it calls on the Swift runtime to create it by specifying the name of the template and any runtime initialization data values that are required to configure the object
    
------

###The Prototype Pattern

####What
The main benefit is to hide the code that creates objects from the components that use them; this means that components don’t need to know which class or struct is required to create a new object, don’t need to know the details of initializers, and don’t need to change when subclasses are created and instantiated. This pattern can also be used to avoid repeating expensive initialization each time a new object of a specific type is created.
   
####Why
The object template pattern provides the foundation for grouping data values and the logic that manipulates them together, known as encapsulation. Encapsulation allows an object to present an API to its consumers while hiding the private implementation of that API. This helps prevent the tight coupling of components.

####How
The prototype pattern uses an existing object—rather than a class or struct—to create new objects. This is often referred to as cloning, since the new object is an identical copy of the existing one, including any changes made to the object’s stored properties that have been made since it was created
    
####Your Moment of Zen
````
func copyWithZone(zone: NSZone) -> AnyObject {
    return Sum(first:self.firstValue,
		second: self.secondValue,
        cache: self.resultsCache);
}
````

------

###The Singleton Pattern

####What
   
####Why

####How
    
####Your Moment of Zen

------

###The Object Pool Pattern

####What
The object pool pattern manages a collection of reusable objects that are provided to calling components. A component obtains an object from the pool, uses it to perform work, and returns it to the pool so that it can be allocated to satisfy future requests. An object that has been allocated to a caller is not available for use by other components until it has been returned to the pool.

####Why
The object pool pattern hides the construction of objects from the components that use them and allows expensive initializations to be amortized through reusing objects repeatedly.

####How
The object pool pattern manages a collection of fungible objects, known as the object pool—or just the pool. Components that need an object borrow one from the pool, use it to perform some work, and then return it to the pool when the work has been completed. Returned objects are then used to satisfy subsequent requests, either from the same component or from another component.
The object pool pattern can be used to manage objects that represent real-world resources and also to amortize expensive initialization procedures by reusing objects to satisfy requests from multiple components.  

####Your Moment of Zen
````
class ProductTableCell: UITableViewCell { // ...statements omitted for brevity...
}
class ViewController: UIViewController, UITableViewDataSource {
@IBOutlet weak var totalStockLabel: UILabel! @IBOutlet weak var tableView: UITableView! var productStore = ProductDataStore();
    override func viewDidLoad() {
        super.viewDidLoad();
        displayStockTotal();
        productStore.callback = {(p:Product) in
            for cell in self.tableView.visibleCells() {
                if let pcell = cell as? ProductTableCell {
                    if pcell.product?.name == p.name {
                        pcell.stockStepper.value = Double(p.stockLevel);
                        pcell.stockField.text = String(p.stockLevel);
                    }
} }
            self.displayStockTotal();
        }
}
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning();
}
    func tableView(tableView: UITableView,
        numberOfRowsInSection section: Int) -> Int {
            return productStore.products.count;
}
func tableView(tableView: UITableView,
cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell { let product = productStore.products[indexPath.row];
let cell = tableView.dequeueReusableCellWithIdentifier("ProductCell")
            as ProductTableCell;
        cell.product = product;
        cell.nameLabel.text = product.name;
        cell.descriptionLabel.text = product.productDescription;
        cell.stockStepper.value = Double(product.stockLevel);
        cell.stockField.text = String(product.stockLevel);
        return cell;
}

@IBAction func stockLevelDidChange(sender: AnyObject) { // ...statements omitted for brevity...
}
    func displayStockTotal() {
        let finalTotals:(Int, Double) = productStore.products.reduce((0, 0.0),
            {(totals, product) -> (Int, Double) in
                return (
                    totals.0 + product.stockLevel,
                    totals.1 + product.stockValue
                );
});
        totalStockLabel.text = "\(finalTotals.0) Products in Stock. "
            + "Total Value: \(Utils.currencyStringFromNumber(finalTotals.1))";
} }
````
------

###Object Pool Variations

####What
   
####Why

####How
    
####Your Moment of Zen

------

###The Factory Method Pattern

####What
   
####Why

####How
    
####Your Moment of Zen

------

###Abstract Factory Pattern

####What
   
####Why

####How
    
####Your Moment of Zen

------

###The Builder Pattern 

####What
   
####Why

####How
    
####Your Moment of Zen

------

    