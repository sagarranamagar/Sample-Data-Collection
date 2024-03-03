 **Hosted on Netlify**
 https://symphonious-platypus-cd4814.netlify.app/


 
I've developed a captivating project using Nuxt.js, an innovative web application framework, that offers users an interactive and engaging experience centered around Southeast Asian (SEA) nations. The project begins by presenting users with a visually appealing interface featuring tiles representing various SEA nations. Upon selecting a nation, users are seamlessly transitioned to the next page where they encounter a dynamically rendered GIF. The uniqueness of the project lies in its approach to user interaction, as it prompts individuals to describe the content of the GIF using their native language.

Users are encouraged to express their thoughts and interpretations of the animated content in a personalized and culturally significant manner. The platform fosters linguistic diversity by allowing users to convey their perceptions in their native languages. Each user's responses are then thoughtfully cataloged and displayed below the interactive interface, creating a rich tapestry of diverse perspectives on the visual content.

This Nuxt.js project not only showcases the versatility of web development but also celebrates the cultural diversity of the Southeast Asian region. Through this engaging and interactive experience, users can connect, share, and appreciate the wealth of linguistic and cultural nuances that make each SEA nation distinctive.



project Structure:
  my-nuxt-sea-project/
|-- assets/
|   |-- images/
|   |-- styles/
|-- components/
|-- layouts/
|-- middleware/
|-- pages/
|   |-- index.vue
|   |-- _country/
|       |-- _id.vue
|-- plugins/
|-- static/
|-- store/
|-- .gitignore
|-- nuxt.config.js
|-- package.json
|-- README.md


Below is a guide for user interaction

1. Landing Page:
Upon entering the website, users will be greeted with an aesthetically pleasing landing page displaying tiles representing Southeast Asian (SEA) nations. Each tile includes the nation's name or flag, inviting users to make a selection.

2. Nation Selection:
Users click on a tile to choose a SEA nation that piques their interest.
After selection, a smooth transition navigates them to a new page where a dynamically rendered GIF related to the chosen nation awaits.

3. Descriptive Interaction:
Users are prompted to describe the content of the GIF in their own words.
A user-friendly form or input field accepts responses, encouraging participants to express themselves freely.
 


# Nuxt 3 Minimal Starter

Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Setup

Make sure to install the dependencies:

```bash
# yarn
yarn install

# npm
npm install

# pnpm
pnpm install
```

## Development Server

Start the development server on `http://localhost:3000`

```bash
npm run dev
```

## Production

Build the application for production:

```bash
npm run build
```

Locally preview production build:


```bash
npm run preview



```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
