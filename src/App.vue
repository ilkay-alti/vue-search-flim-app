<template>
  <header>
    <router-link to="/">
      <h1><span>Film</span>App</h1>
    </router-link>
  </header>
  <main>
    <router-view />
  </main>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Fira+Sans:wght@300;400;500;700&display=swap");
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}
body {
  background-color: #222831;
}
header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px auto;
  background-color: #393e46;
  height: 100px;
}

a {
  text-decoration: none;
  color: white;
}
span {
  color: #00adb5;
}
main {
  margin: 0 10%;
  align-items: center;
  justify-content: center;
}
</style>
