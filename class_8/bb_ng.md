#Backbone and Angular

- [MVC Design Pattern](http://blog.codinghorror.com/understanding-model-view-controller/)
- [MOVE Design Pattern](http://cirw.in/blog/time-to-move-on)

## Tutorials
- [Angular Videos](https://egghead.io/)
- [Backbone Tutorial](http://adrianmejia.com/blog/2012/09/11/backbone-dot-js-for-absolute-beginners-getting-started)

##Code Snippets

### Angular

ng.html
```html
<!doctype html>
<html ng-app>
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.0-beta.7/angular.min.js"></script>
    <script src="ngTabs.js"></script>
    <link rel="stylesheet" href="ngTabs.css">
  </head>
  <body>
    <h2>Tabs</h2>
    <div ng-controller="NgTabsCtrl">
      <div ng-show="tabs.length === 0">
        Loading...
      </div>
      <div ng-show="tabs.length > 0">
        <div ng-repeat="tab in tabs">
          <div class="tab" ng-class="{active: tab.name === activeTab.name}">
            <a class="tab-link" href="#" ng-click="showTab(tab)">{{tab.name}}</a>
            <div class="hidden">{{tab.content}}</div>
          </div>
        </div>
        <div class="active-tab-content">
          {{activeTab.content}}
        </div>
      </div>
    </div>
  </body>
</html>
```

ng.js
```javascript
function NgTabsCtrl($scope, $http) {
  
  $scope.tabs = [];

  $http({method: 'GET', url: 'http://rs.hankyates.com:3000/content'})
    .success(onTabsFetched);

  $scope.showTab = function(tab){
    $scope.activeTab = tab;
  };

  function onTabsFetched(tabs){
    $scope.tabs = tabs;
    $scope.activeTab = $scope.tabs[0];
  }

};
```

### Backbone

```html
<!doctype html>
<html class="no-js">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>Ajax Tabs Using Backbone</title>
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="app.css">
    </head>
    <body>
        <div id="tabs-app">
            <div class="hide-on-load">Loading...</div>
            <div class="show-on-load">
                <div class="tabs"></div>
                <div class="active-tab-content"></div>
            </div>
        </div>
        <script src="http://cdnjs.cloudflare.com/ajax/libs/underscore.js/1.6.0/underscore-min.js"></script>
        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js"></script>
        <script src="http://cdnjs.cloudflare.com/ajax/libs/backbone.js/1.1.2/backbone-min.js"></script>
        <script src="app.js"></script>
        <script type="text/template" id="tab-template">
            <div class="tab">
                <a href="#" class="tab-link"><%= name %></a>
                <div class="tab-content hidden"><%= content %></div>
            </div>
        </script>
    </body>
</html>
```

```javascript
$(function(){

	var TabModel = Backbone.Model.extend({
		defaults: {
			name: 'Unnamed Tab',
			content: 'Tab content not specified.'
		}
	});

	var TabsCollection = Backbone.Collection.extend({
		model: TabModel,
		url: 'http://rs.hankyates.com:3000/content'
	});

	var TabView = Backbone.View.extend({

		template: _.template($('#tab-template').html()),

		initialize: function(){
			this.render();
		},

		render: function(){
			this.$el.html(this.template(this.model.attributes));
	   		return this;
		}
	});

	var AppView = Backbone.View.extend({

		el: '#tabs-app',

		events: {
			'click .tab-link': 'tabClickHandler'
		},

		initialize: function(){
			var self = this;
			this.$tabsList = this.$('.tabs');
			this.$activeTabContent = this.$('.active-tab-content');
			this.tabs = new TabsCollection;
			this.listenTo(this.tabs, 'add', this.addTab);
			this.tabs.fetch({ success: function(){
				self.render();
			}});
		},

		render: function(){
			var $firstTab = $('.tab').first();
			this.activateTab($firstTab);
			this.$el.addClass('loaded');
		},
		
		addTab: function(tab){
			var tabView = new TabView({ model: tab });
			this.$tabsList.append(tabView.el);
		},

		tabClickHandler: function(e){
			e.preventDefault();
			this.activateTab($(e.target).closest('.tab'));
		},

		activateTab: function($tab){
			var tabContent = $tab.find('.tab-content').html(),
				$allTabs = this.$el.find('.tab');

			this.$activeTabContent.html(tabContent);
			
			$allTabs.removeClass('active');

			$tab.addClass('active');
		}


	});

	new AppView();

});
```
