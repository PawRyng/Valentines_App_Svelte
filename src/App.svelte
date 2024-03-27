<script lang="ts">
  import { Router, Route } from "svelte-routing";

  //import settings
  import settings from "./Data/settings.json"
  //import views
  import Home from "./Routers/Home.svelte";
  import Finish from "./Routers/Finish.svelte";
  import Admin from "./Routers/Admin.svelte";
  //styles
  import './Style/Views/Main.css';

</script>

<Router>
  <Route path="/" component={Home} />
  <Route path="/">
    <Home />
  </Route>
  <Route path={`/${settings.ok.url}`} component={Finish} />
  <Route path={`/${settings.ok.url}`}>
    <Finish/>
  </Route>
  <Route path={`/${settings.admin.url}`} component={Admin} />

</Router>

