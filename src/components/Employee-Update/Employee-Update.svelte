<script context="module">

	export async function preload({params}) {
		const {id} = params;
		return {id};
	}

</script>

<script>
	export let id;
	var employee_details = JSON.parse(localStorage.getItem('employeeDB')).find((ele)=> {
					return ele.id == id;
				});
	var employees = JSON.parse(localStorage.getItem('employeeDB'));
	
	var username = employee_details.username;
	var emailid = employee_details.emailid;
	var phonenumber = employee_details.phonenumber;
	var age = employee_details.age;
	var name = employee_details.name;
	
	function updateEmployee() {
				var emp_details  = {
					username: username,
					id: id,
					name: name,
					age: age,
					phonenumber: phonenumber,
					emailid: emailid
				}

				for (let i = 0; i < employees.length; i++) {

					if (employees[i].id == id) {
						employees[i] = emp_details;
					}
				}

				localStorage.setItem("employeeDB", JSON.stringify(employees));
				window.location = "/";
			}
</script>

<div class="p-5 container-fluid">
	<div class="d-flex justify-content-start align-items-center">
		<i class="fas fa-school" />
		<h3 class="m-2 text-dark">Update Employee</h3>
	</div>

	<div class="row align-items-center">
		<div class="p-2 d-md-block col-lg-6 mx-auto">
			<div class="shadow border-0 card p-4">
				<div class="card-body">
					<h4 class="text-dark mb-3">Update Employee Details</h4>

					<div class="input-group mb-3">
						<span
							class="shadow rounded-left border-0 input-group-text bg-white"
							id="basic-addon1"
						>
							<i class="fas fa-book-open" />
						</span>
						<input
							type="text"
							bind:value={username}
							class="shadow rounded-right border-0 form-control"
							placeholder="Employee User Name"
						/>
					</div>
					<div class="input-group mb-3">
						<span
							class="shadow rounded-left border-0 input-group-text bg-white"
							id="basic-addon1"
						>
							<i class="fas fa-book-open" />
						</span>
						<input
							bind:value={name}
							type="text"
							class="shadow rounded-right border-0 form-control"
							placeholder="Employee Name"
						/>
					</div>
					<div class="input-group mb-3">
						<span
							class="shadow rounded-left border-0 input-group-text bg-white"
							id="basic-addon1"
						>
							<i class="fas fa-chalkboard-teacher" />
						</span>
						<input
							type="text"
							bind:value={phonenumber}
							class="shadow rounded-right border-0 form-control"
							placeholder="Employee Phone Number"
						/>
					</div>

					<div class="input-group mb-3">
						<span
							class="shadow rounded-left border-0 input-group-text bg-white"
							id="basic-addon1"
						>
							<i class="far fa-clock" />
						</span>
						<input
							type="text"
							bind:value={age}
							class="shadow rounded-right border-0 form-control"
							placeholder="Age"
						/>
					</div>

					<div class="input-group mb-3">
						<span
							class="shadow rounded-left border-0 input-group-text bg-white"
							id="basic-addon1"
						>
							<i class="far fa-clock" />
						</span>
						<input
							type="text"
							bind:value={emailid}
							class="shadow rounded-right border-0 form-control"
							placeholder="Email ID"
						/>
					</div>
					<div class="row">
						<div class="col-6">
							<button
								type="button"
								on:click={updateEmployee}
								class="shadow border-0 rounded-0 btn btn-primary px-4"
							>
								Update Employee
							</button>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>
