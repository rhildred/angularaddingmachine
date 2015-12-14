[Angular adding machine](https://github.com/rhildred/angularaddingmachine)
=====

This is a short UI for adding a string of amounts:

```
    <body>
        <div ng-app="myApp" ng-controller="myCtrl">
            <div ng-repeat="(n, listAmount) in amounts track by n">{{listAmount}}</div>
            <form><p>Amount : <input type="text" ng-model="currentAmount"></p>
                <button type = "submit" ng-click="addAmountAndTotal()">Add</button>
            </form>
            <p>Total: {{total}}</p>
        </div>

    </body>
```

The new piece here is repetition in the UI. The Angular Directive ng-repeat is used. Angular is also used to provide behaviour:

```

    <script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js"></script>
    <script>
        angular.module("myApp", []).controller("myCtrl", function ($scope) 
                                               {
            // this will hold the amounts that are entered
            $scope.amounts =  [];

            //define what happens when the button is clicked
            $scope.addAmountAndTotal = function()
            {
                $scope.amounts.push($scope.currentAmount);
                $scope.currentAmount = "";
                $scope.total = 0;
                for(var n = 0; n < $scope.amounts.length; n++)
                {
                    $scope.total += Number($scope.amounts[n]);
                }
            };
        });
    </script>


```

You can see the [project in action here](https://rhildred.github.io/angularaddingmachine). 
