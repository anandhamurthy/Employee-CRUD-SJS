<script>
	import { Router, Link, Route } from "svelte-routing";

	var employees = localStorage.getItem('employeeDB') === null | undefined ? [] : JSON.parse(localStorage.getItem('employeeDB'));

			function goToCreate() {
				this.window.location = "/create-employee";
			}
			function goToView(id) {
				window.location = "/view-employee/" + id
			}
			function Delete(id) {
				employees = employees.filter((ele) => {
					return ele.id != id;
				});
				localStorage.setItem("employeeDB", JSON.stringify(employees))
			}
			function goToUpdate(id) {
				window.location = "/update-employee/" + id
			}
</script>

<div>
	<div>
		<nav class="navbar navbar-expand-lg navbar-light bg-light">
			<a class="navbar-brand mx-2" href="#">Employee CRUD APP</a>
			<button
				class="navbar-toggler"
				type="button"
				data-toggle="collapse"
				data-target="#navbarText"
				aria-controls="navbarText"
				aria-expanded="false"
				aria-label="Toggle navigation"
			>
				<span class="navbar-toggler-icon" />
			</button>
			<div class="collapse navbar-collapse" id="navbarText">
				<div
					class="d-flex flex-wrap justify-content-end"
					style="width: 100%"
				>
					<Link to="/create-employee">
						<button class="btn btn-primary btn-sm mx-2">
							Add Employee
						</button>
					</Link>
				</div>
			</div>
		</nav>
		<div class="container">
			<div class="py-4">
				<table class="table border shadow">
					<thead class="thead-dark">
						<tr>
							<th scope="col">#ID</th>
							<th scope="col">Name</th>
							<th scope="col">Username</th>
							<th scope="col">Age</th>
							<th scope="col">Phone Number</th>
							<th scope="col">Email</th>
							<th>Action</th>
						</tr>
					</thead>
					<tbody>
						{#each employees as emp, index}
							<tr>
								<th scope="row">{emp.id}</th>
								<td>{emp.name}</td>
								<td>{emp.username}</td>
								<td>{emp.age}</td>
								<td>{emp.phonenumber}</td>
								<td>{emp.emailid}</td>
								<td>
									<button
										on:click={() => goToView(emp.id)}
										class="btn btn-primary btn-sm mx-2"
									>
										View
									</button>
									<button
										on:click={() => goToUpdate(emp.id)}
										class="btn btn-primary btn-sm mx-2"
									>
										Edit
									</button>
									<button
										on:click={() => Delete(emp.id)}
										class="btn btn-primary btn-sm mx-2"
									>
										Delete
									</button>
								</td>
							</tr>
						{/each}
					</tbody>
				</table>
			</div>
		</div>
	</div>
</div>
