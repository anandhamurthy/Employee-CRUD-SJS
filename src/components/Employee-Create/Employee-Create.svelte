<script>
	var username = "", name = "", phonenumber = "", emailid = "", age = "";

	var employees = localStorage.getItem('employeeDB') === null | undefined ? [] : JSON.parse(localStorage.getItem('employeeDB'));
	
	function createEmployee() {
		
		var employee = {
					username: username,
					id: Date.now(),
					name: name,
					age: age,
					phonenumber: phonenumber,
					emailid: emailid
				}
				 employees.push(employee);
				 localStorage.setItem("employeeDB", JSON.stringify(employees));
				 window.location = "/";
	}

</script>

<div class="p-5 container-fluid">
	<div class="d-flex justify-content-start align-items-center">
		<i class="fas fa-school" />
		<h3 class="m-2 text-dark">Create Employee</h3>
	</div>

	<div class="row align-items-center">
		<div class="p-2 d-md-block col-lg-6 mx-auto">
			<div class="shadow border-0 card p-4">
				<div class="card-body">
					<h4 class="text-dark mb-3">Add Employee Details</h4>

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
							type="text"
							bind:value={name}
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
								on:click={createEmployee}
								class="shadow border-0 rounded-0 btn btn-primary px-4"
							>
								Add Employee
							</button>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>
