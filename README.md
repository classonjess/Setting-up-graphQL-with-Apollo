# Setting-up-graphQL-with-Apollo

Using GraphQL Apollo client to fetch data for a restaurant app.

In the main directory:
- npm install.
- followed by npm run dev.
- Naivagtion to localhost:3000

In the backend directory:
- nvm install 12.0.0.
- npm install.
- npm run build.
- npm run develop.

navigate to localhost:1337/admin and signup in Strapi

- Go to roles and permissions, select the public and add the user you have created.
- Add your restaurants.
- Navigate into Restaurants and fill in Name, Description and upload an image.

Learning where the Apollo Client pattern is used:
With the Apollo Client, you can easily determine the state of the HTTP calls between your UI and DAL. In the example below, the GQL query can return “loading,” “error,” or “data,” depending on which one is the correct response. This allows for each state to be handled with a short code

import { gql, useQuery } from '@apollo/client';
 
const Username = () => {
  const { loading, error, data } = useQuery(gql`
    {
      me {
        username
      }
    }
  `);
 
  if (loading) return <text>Loading...</text>;
  if (error) return (
    <text>Error! ${error.message}</text>
  );
  if (!data || !data.user) return (
    <text>Could not find user :(</text>
  );
 
  return (
    <text>Your username: {data.me.username}</text>
  );
}
