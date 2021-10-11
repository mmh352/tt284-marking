<script lang="ts">
	import { writable, derived } from 'svelte/store';

	const p1f1Implementation = writable(0);
	const p1f1Functionality = writable(0);
	const p1f1CodeQuality = writable(0);
	const p1f1Documentation = writable(0);
	const p1f1Total = derived([p1f1Implementation, p1f1Functionality, p1f1CodeQuality, p1f1Documentation], ([p1f1Implementation, p1f1Functionality, p1f1CodeQuality, p1f1Documentation]) => {
		return p1f1Implementation + p1f1Functionality + p1f1CodeQuality + p1f1Documentation;
	});
	const p1f2Implementation = writable(0);
	const p1f2Functionality = writable(0);
	const p1f2CodeQuality = writable(0);
	const p1f2Documentation = writable(0);
	const p1f2Total = derived([p1f2Implementation, p1f2Functionality, p1f2CodeQuality, p1f2Documentation], ([p1f2Implementation, p1f2Functionality, p1f2CodeQuality, p1f2Documentation]) => {
		return p1f2Implementation + p1f2Functionality + p1f2CodeQuality + p1f2Documentation;
	});
	const p1f3Implementation = writable(0);
	const p1f3Functionality = writable(0);
	const p1f3CodeQuality = writable(0);
	const p1f3Documentation = writable(0);
	const p1f3Total = derived([p1f3Implementation, p1f3Functionality, p1f3CodeQuality, p1f3Documentation], ([p1f3Implementation, p1f3Functionality, p1f3CodeQuality, p1f3Documentation]) => {
		return p1f3Implementation + p1f3Functionality + p1f3CodeQuality + p1f3Documentation;
	});
	const p1Total = derived([p1f1Total, p1f2Total, p1f3Total], ([p1f1Total, p1f2Total, p1f3Total]) => {
		return p1f1Total + p1f2Total + p1f3Total;
	});
	const p2Standards = writable(0);
	const p2Accessibility = writable(0);
	const p2Total = derived([p2Standards, p2Accessibility], ([p2Standards, p2Accessibility]) => {
		return p2Standards + p2Accessibility;
	});
	const p3PostMortem = writable(0);
	const p3Total = derived([p3PostMortem], ([p3PostMortem]) => {
		return p3PostMortem;
	});
	const total = derived([p1Total, p2Total, p3Total], ([p1Total, p2Total, p3Total]) => {
		return p1Total + p2Total + p3Total;
	});
</script>

<main>
	<h1>TMA01</h1>
	<h2>Part 1</h2>
	<table>
		<thead>
			<tr>
				<th>Feature</th>
				<th>Implementation</th>
				<th>Functionality</th>
				<th>Code Quality</th>
				<th>Documentation</th>
				<th>Total</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Header</td>
				<td><input type="number" min="0" max="5" bind:value={$p1f1Implementation}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f1Functionality}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f1CodeQuality}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f1Documentation}/></td>
				<td>{$p1f1Total}</td>
			</tr>
			<tr>
				<td>Main Content</td>
				<td><input type="number" min="0" max="5" bind:value={$p1f2Implementation}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f2Functionality}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f2CodeQuality}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f2Documentation}/></td>
				<td>{$p1f2Total}</td>
			</tr>
			<tr>
				<td>News Sidebar</td>
				<td><input type="number" min="0" max="5" bind:value={$p1f3Implementation}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f3Functionality}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f3CodeQuality}/></td>
				<td><input type="number" min="0" max="5" bind:value={$p1f3Documentation}/></td>
				<td>{$p1f3Total}</td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td>Part 1 Total</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>{$p1Total}</td>
			</tr>
		</tfoot>
	</table>
	<h2>Part 2</h2>
	<table>
		<thead>
			<tr>
				<th>Feature</th>
				<th>Total</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Standards Compliance</td>
				<td><input type="number" min="0" max="15" bind:value={$p2Standards}/></td>
			</tr>
			<tr>
				<td>Accessibility</td>
				<td><input type="number" min="0" max="15" bind:value={$p2Accessibility}/></td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td>Total</td>
				<td>{$p2Total}</td>
			</tr>
		</tfoot>
	</table>
	<h2>Part 3</h2>
	<table>
		<thead>
			<tr>
				<th>Feature</th>
				<th>Total</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Post Mortem</td>
				<td><input type="number" min="0" max="15" bind:value={$p3PostMortem}/></td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td>Total</td>
				<td>{$p3Total}</td>
			</tr>
		</tfoot>
	</table>
	<h2>Overall total</h2>
	<p>{$total}</p>
</main>

<style>
</style>
