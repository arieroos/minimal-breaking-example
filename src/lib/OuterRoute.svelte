<script>
    import {Route, Router} from "svelte-routing";

    console.log("Loading Outer")
</script>

Outer Stuff

<Router basepath={"outer"}>
  <Route>
    <div>
      <!-- Links to an inner component that displays some cool data from the database -->
    </div>
  </Route>
  <Route let:params path=":inner">
    <!-- In here I have a reference to another Svelte component that uses the value of inner -->
  </Route>
</Router>
