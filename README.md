                                      CURRING IN JS :

   Currying is a JavaScript functional programming approach that turns a function with several parameters into a series of functions that only accept one argument each. This makes it possible to create functions in a more flexible way and may result in code that is clearer and more reusable.

                                      Benefits of Currying :

                        Partial Application: It is possible to construct a function with pre-filled arguments.
Reusability: A general function can be used to construct customized functions.
Better Readability: By lowering the quantity of parameters in a single function call, currying can help code become more understandable.

CODE:

function checkout(product) {
    return function(quantity) {
        return function(discountCode) {
            
            const prices = {
                'laptop': 1000,
                'phone': 500,
                'tablet': 750
            };

            
            const discounts = {
                'SUMMER10': 0.10,   
                'SAVE20': 0.20,     
                'NO_DISCOUNT': 0
            };

        
            const basePrice = prices[product] * quantity;
            const discount = discounts[discountCode] || 0;
            const totalPrice = basePrice - (basePrice * discount);

            return `Product: ${product}, Quantity: ${quantity}, Discount: ${discountCode}, Total Price: $${totalPrice.toFixed(2)}`;
        };
    };
}


const productSelected = checkout('laptop');         
const quantitySelected = productSelected(2);       
const finalPrice = quantitySelected('SAVE20');     

console.log(finalPrice);

// Output: "Product: laptop, Quantity: 2, Discount: SAVE20, Total Price: $1600.00"
