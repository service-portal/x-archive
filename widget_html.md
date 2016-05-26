#### Widget HTML
This is where the HTML markup for your widget goes. Inside the template , you can leverage AngularJS’s two-way binding to bind your controller variables to your markup. It uses the `controllerAs c` syntax for basic binding.
```html
<div>
  ${Symbol Lookup}: 
  <input ng-model="c.data.symbol" 
    ng-model-options="{debounce: 750}" ng-change="c.update()" placeholder="Type stock symbol" />
  <div ng-show="c.data.symbol" style="font-size: 2em;">        
    <p>${Stock Price}: 
  	  <span ng-if="!c.data.price">${Requesting stock price}</span><span>{{c.data.price | currency:"$"}}</span>
    </p>
    <img ng-src="http://chart.finance.yahoo.com/z?s={{c.data.symbol}}&t=1d&z=l" />
  </div>
</div>
```
