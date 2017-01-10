# Ember Routing Diagnostic

Record your responses inside the fenced code blocks below each question.

1.  What are the main task(s) you perform inside the Ember Application Router,
    and what are the main task(s) you perform inside an Ember Route?

    ```md
    The router matches url paths to pods inside the app directory. The route file connects that url to a template, a model, and any actions that need to be associated with it
    ```

1.  What is the command to generate a route named `boston` nested under
    `campus`?

    ```md
    ember g route campus/boston
    ```

1.  Suppose you have a nested route at the URL `/campus/boston`. How would you
    use the `link-to` helper to generate an appropriate link?

    ```md
    {{#link-to 'campus/boston'}}Boston Campus{{/link-to}}
    ```

1.  Explain **at least** two differences between the following two route
    definitions.

    ```js
    this.route('products', function () {
      this.route('product', { path: '/:product_id' }); // <= 👀here
    });

    this.route('product', { path: '/products/:product_id' }); // <= 👀 here
    ```

    ```md
    The first actually creates 2 routes -- the path '[domain]/products' renders the 'products' template, and the path '[domain]/products/[product id]' renders the products template, with the product template appearing inside that page (wherever the {{outlet}} tag appears)

    The second simply routes from '[domain]/products/[product id]' to the product template.

    So, first difference: the nested route creates two different url routes,

    and second, the nested route has the product template nested inside the products template, while the single line just renders the product template at the appropriate url
    ```

1.  Suppose we have the following route definition:

    ```js
    this.route('movie', { path: '/movies/:movie_id' }); // <= 👀 here
    ```

    If we navigate in the browser to `/movies/123`, how can we reference the
    value `'123'` inside a Route?

    ```md
    export default Ember.Route.extend({
      model (params) {
        someCode(params.movie_id);
      }
    });

    params.movie_id, in this case, takes the value 123
    ```

1.  Inside a template, how do we reference data provided by a Route?

    ```md
It comes in under the variable `model` -- so if it's an array, you could, for example, do this:

``{{#each model as |element|}}
  <p>here's my {{element}}</p>
{{/each}}``

or if it's an object,

{{model.attribute}}
    ```
