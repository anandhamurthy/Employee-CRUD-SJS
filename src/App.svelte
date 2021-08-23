<script>

import { Router, Route } from "svelte-routing";
  import Create from "./components/Employee-Create/Employee-Create.svelte";
  import Update from "./components/Employee-Update/Employee-Update.svelte";
  import SingleView from "./components/Employee-Single-View/Employee-Single-View.svelte";
  import View from "./components/Employee-View/Employee-View.svelte";

  export let url = "";
</script>

<Router {url}>
	<div>
		<Route path="create-employee/" component={Create} />
		<Route path="update-employee/:id" component={Update} />
		<Route path="view-employee/:id" component={SingleView} />
		<Route path="employees/" component={View} />
		<Route path="/" component={View} />
	</div>
</Router>
