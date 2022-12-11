<script>
	import axios from 'axios'
	import RefreshIcon from '../assets/refresh.png'
	import { computed } from "vue";


	export default {
		name: 'UserView',
		data() {
			return {
                firstName: "",
                lastName: "",
                image: null,
                gender: null,
                country: null,
                email: null,
                cell: null,
                phone: null
			}
		},

        methods: {

        },

        mounted() {
            this.firstName = computed(() => this.$route.query.firstName)
            this.lastName = computed(() => this.$route.query.lastName)
            this.image = computed(() => this.$route.query.image)
            this.gender = computed(() => this.$route.query.gender)
            this.country = computed(() => this.$route.query.country)
            this.email = computed(() => this.$route.query.email)
            this.cell = computed(() => this.$route.query.cell)
            this.phone = computed(() => this.$route.query.phone)
        },

		render() {
			return (
                <div class="mainDiv">
					<div class="titleDiv">
						User Details
					</div>

                    <div className="tableImageContainer">
                        <img className="userImageLarge" src={this.image} alt="profile picture" />
                    </div>

                    <table className="userTable">
                        <tr className="tableRow">
                            <td className="tableHeader">
                                Name:
                            </td>

                            <td className="tableDescription">
                                {this.firstName} {this.lastName}
                            </td>
                        </tr>

                        <tr className="tableRow">
                            <td className="tableHeader">
                                Gender:
                            </td>

                            <td className="tableDescription">
                                {this.gender}
                            </td>
                        </tr>

                        <tr className="tableRow">
                            <td className="tableHeader">
                                Country:
                            </td>

                            <td className="tableDescription">
                                {this.country}
                            </td>
                        </tr>

                        <tr className="tableRow">
                            <td className="tableHeader">
                                Email:
                            </td>

                            <td className="tableDescription">
                                {this.email}
                            </td>
                        </tr>

                        <tr className="tableRow">
                            <td className="tableHeader">
                                Phone no:
                            </td>

                            <td className="tableDescription">
                                {this.phone}
                            </td>
                        </tr>

                        <tr className="tableRow">
                            <td className="tableHeader">
                                Cell no:
                            </td>

                            <td className="tableDescription">
                                {this.cell}
                            </td>
                        </tr>
                    </table>

                    <button className="backButton" onClick={()=>{
                        this.$router.push({name: "home"})
                    }}>
                        Back
                    </button>
                </div>
            )
        }
    }
</script>