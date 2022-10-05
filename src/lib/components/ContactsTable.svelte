<script>
	import { enhance } from '$app/forms';
	export let contacts = [];
</script>

<div class="overflow-x-auto w-full mt-6">
	<table class="table w-full">
		<!-- head -->
		<thead>
			<tr>
				<th>
					<label>
						<input type="checkbox" class="checkbox" />
					</label>
				</th>
				<th>Name</th>
				<th>Job</th>
				<th>Email</th>
				<th />
			</tr>
		</thead>
		<tbody>
			{#each contacts as contact}
				<tr>
					<th>
						<label>
							<input type="checkbox" class="checkbox" />
						</label>
					</th>
					<td>
						<div class="flex items-center space-x-3">
							<div class="avatar">
								<div class="mask mask-squircle w-12 h-12">
									<img src="https://i.pravatar.cc/150?u={contact.name}" alt={contact.name} />
								</div>
							</div>
							<div>
								<div class="font-bold">{contact.name}</div>
							</div>
						</div>
					</td>
					<td>
						{contact.company}
						<br />
						<span class="badge badge-ghost badge-sm">{contact.job}</span>
					</td>
					<td>{contact.email}</td>
					<th>
						<form method="POST" action="?/delete" use:enhance>
							<input type="hidden" name="id" hidden value={contact.id} />
							<button class="btn btn-error text-white btn-xs">Delete</button>
						</form>
					</th>
				</tr>
			{/each}
		</tbody>
		<!-- foot -->
		<tfoot>
			<tr>
				<th />
				<th>Name</th>
				<th>Job</th>
				<th>Email</th>
				<th />
			</tr>
		</tfoot>
	</table>
</div>
