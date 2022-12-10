<template>
  <router-view/>
</template>

<style>
body {
  background-color: rgb(224, 224, 224);
  overflow: hidden;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #575757;
  font-size: 16px;
  width: 100%;
  display: flex;
	justify-content: center;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.mainDiv {
  position: absolute;
  margin-top: 30px;
  margin-bottom: 30px;
  width: 90vw;
}

@media (min-width: 600px) {
	.mainDiv {
		width: 50vw;
	}
}

@media (min-width: 992px) {
	.mainDiv {
		width: 36vw;
	}
}

.titleDiv {
  font-size: 1.5em;
  font-weight: bold;
}

.searchDiv {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px 10px;
  margin-top: 25px;
}

.searchBar {
  width: 100%;
  margin-right: 15px;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid grey;
}

.refreshIcon {
  width: 20px;
  height: 20px;
  cursor: pointer;
}

.userListDiv {
  display: flex;
  flex-direction: column;
  padding: 15px 10px;
}

.userDiv {
	background-color: rgb(236, 232, 232);
	border: 2px solid rgb(177, 177, 177);
	border-radius: 6px;
	display: flex;
	padding: 10px 12px;
	margin-top: 15px;
	font-size: 25px;
  cursor: pointer;
  transition: all 0.35s;
}

.userDiv:active,
.userDiv:hover {
    border: 2px solid rgb(51, 51, 51)
}

.userDetailsDiv {
  padding: 10px 5px;
}

.userImage {
  width: 100px;
	height: 100px;
	object-fit: cover;
	margin-right: 10px;
	background-color: white;
	border: 1px solid rgb(209, 207, 207);
}

.userSpan {
  font-weight: bold;
}

.userSubDiv {
  width: 100%;
  font-size: 0.95rem;
	line-height: 1.3em;
  text-align: left;
}

.overflowDiv {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 280px;
}

@media (min-width: 600px) {
	.overflowDiv {
    max-width: 300px;
  }
}

@media (min-width: 992px) {
	.overflowDiv {
    max-width: 400px;
  }
}
</style>
