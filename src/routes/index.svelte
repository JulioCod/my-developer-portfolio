
<script context="module">
  import { client } from '$lib/graphql-client';
  import { gql } from 'graphql-request';



  export const load = async () => {

    const query = gql`
      query GetProjects {
        projects {
          name
          slug
          description
          demo
          sourceCode
          image {
            url
          }
        }
      }
    `

    const { projects } = await client.request(query)

    return {
      props: {
        projects,
      },
    }

  }
</script>

<script>
  export let projects
</script>

<pre>{JSON.stringify(projects, null, 2)}</pre>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
