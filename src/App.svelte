<script>
  import {Link, Route, Router} from "svelte-routing";

  async function loadComponent(compName) {
      console.log("Loading component")

      let comp
      switch (compName) {
          case "outer":
              comp = (await import('./lib/OuterRoute.svelte')).default
              break
          default:
              console.error("Unknown tab: " + compName)
      }

      return comp
  }
</script>

<main>
  <div>
    <Router>
      <nav>
        <Link to="/outer">Outer Route</Link>
      </nav>

      <Route let:params path="/:component/*">
        {#await loadComponent(params.component) then Comp}
          <Comp/>
        {/await}
      </Route>
    </Router>
  </div>
</main>
