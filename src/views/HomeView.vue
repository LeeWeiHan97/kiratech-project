<script>
	import axios from 'axios'
	import RefreshIcon from '../assets/refresh.png'
	import { computed } from "vue";


	export default {
		name: 'HomeView',

		data() {
			return {
				originalUserList: [],
				userList: [],
				search: ""
			}
		},

		methods: {
			getUser() {
				axios
					.get('https://randomuser.me/api/?results=20')
					.then(async response => {
						console.log(response.data.results)
						this.originalUserList = computed(() => response.data.results)
						this.userList = computed(() => response.data.results)
					})
			},

			filterUserList(search) {
				this.search = computed(() => search)

				// if user removes search, return the original fetched list
				if (!search || search.trim() === "" || search === null) {
					this.userList = computed(() => this.originalUserList)
					return
				}

				let filteredList = []
				for (var user of this.userList) {
					if (user.name.first.toLowerCase().includes(search) || user.name.last.toLowerCase().includes(search)) {
						filteredList.push(user)
					}
				}

				this.userList = computed(() => filteredList)
			}
		},

		beforeMount() {
			this.getUser()
		},

		render() {
			return (
				<div class="mainDiv">
					<div class="titleDiv">
						Users
					</div>

					<div class="searchDiv">
						<input class="searchBar" value={this.search} placeholder="Search for users here..." onInput={(e)=>{
							this.filterUserList(e.target.value)
						}} />

						<img src={RefreshIcon} class="refreshIcon" onClick={()=>{
							this.getUser()
						}} />
					</div>

					<div class="userListDiv">
						{
							this.userList && this.userList.length > 0 ?

							this.userList.map((user) => {
								return (
									<div class="userDiv" onClick={()=>{}}>
										<img class="userImage" src={user.picture.medium} alt={user.name.first} />
										
										<div class="userDetailsDiv">
											<div class="userSubDiv">
												<span class="userSpan">Name:</span> {user.name.title} {user.name.first} {user.name.last}
											</div>

											<div class="userSubDiv">
												<span class="userSpan">Gender:</span> {user.gender}
											</div>

											<div class="userSubDiv">
												<span class="userSpan">Country:</span> {user.location.country}
											</div>

											<div class="userSubDiv overflowDiv">
												<span class="userSpan">Email:</span> {user.email}
											</div>
										</div>
									</div>
								)
							}) : null
						}
					</div>
				</div>
			)
		}
	}
</script>