<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import * as Card from '$lib/components/ui/card/index.js';
	import { Input } from '$lib/components/ui/input/index.js';
	import { Label } from '$lib/components/ui/label/index.js';
	import { Separator } from '$lib/components/ui/separator';

	let sysAverage: number = 120;
	let diaAverage: number = 80;
	let pulseAverage: number = 90;

	function calculateAverage(a: any, b: any, c: any): number {
		a = parseInt(a);
		b = parseInt(b);
		c = parseInt(c);
		return Math.round((a + b + c) / 3);
	}

	function calculateBloodPressure() {
		sysAverage = calculateAverage(
			measurements[0].sys as number,
			measurements[1].sys as number,
			measurements[2].sys as number
		);
		diaAverage = calculateAverage(
			measurements[0].dia as number,
			measurements[1].dia as number,
			measurements[2].dia as number
		);
		pulseAverage = calculateAverage(
			measurements[0].pulse as number,
			measurements[1].pulse as number,
			measurements[2].pulse as number
		);
	}

	let measurements = [
		{
			sys: 120,
			dia: 80,
			pulse: 90
		},
		{
			sys: 120,
			dia: 80,
			pulse: 90
		},
		{
			sys: 120,
			dia: 80,
			pulse: 90
		}
	];
</script>

<Card.Root class="dark w-full max-w-sm">
	<Card.Header>
		<div class="flex h-full w-full items-center justify-center gap-3 p-4">
			<svg width="48" height="48" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"
				><path
					fill="#f87171"
					opacity="0.75"
					d="M9 2H5v2H3v2H1v6h2v2h2v2h2v2h2v2h2v2h2v-2h2v-2h2v-2h2v-2h2v-2h2V6h-2V4h-2V2h-4v2h-2v2h-2V4H9zm0 2v2h2v2h2V6h2V4h4v2h2v6h-2v2h-2v2h-2v2h-2v2h-2v-2H9v-2H7v-2H5v-2H3V6h2V4z"
				/></svg
			>
			<svg width="48" height="48" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"
				><path
					fill="#f87171"
					d="M9 2H5v2H3v2H1v6h2v2h2v2h2v2h2v2h2v2h2v-2h2v-2h2v-2h2v-2h2v-2h2V6h-2V4h-2V2h-4v2h-2v2h-2V4H9zm0 2v2h2v2h2V6h2V4h4v2h2v6h-2v2h-2v2h-2v2h-2v2h-2v-2H9v-2H7v-2H5v-2H3V6h2V4z"
				/></svg
			>
			<svg width="48" height="48" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"
				><path
					fill="#f87171"
					opacity="0.75"
					d="M9 2H5v2H3v2H1v6h2v2h2v2h2v2h2v2h2v2h2v-2h2v-2h2v-2h2v-2h2v-2h2V6h-2V4h-2V2h-4v2h-2v2h-2V4H9zm0 2v2h2v2h2V6h2V4h4v2h2v6h-2v2h-2v2h-2v2h-2v2h-2v-2H9v-2H7v-2H5v-2H3V6h2V4z"
				/></svg
			>
		</div>

		<Card.Title class="text-center text-2xl">Blood Pressure</Card.Title>
		<Card.Description class="text-center">Input three measurements for the median</Card.Description>
	</Card.Header>
	<Card.Content class="flex flex-col gap-8">
		<Separator />
		{#each measurements as measure}
			<section class="flex gap-4">
				<div class="grid gap-2">
					<Label for="sys">SYS</Label>
					<Input
						id="sys"
						type="number"
						placeholder="120"
						required
						bind:value={measure.sys}
						on:change={calculateBloodPressure}
					/>
					<p class=" text-sm text-muted-foreground">mmHg</p>
				</div>
				<div class="grid gap-2">
					<Label for="dia">DIA</Label>
					<Input
						id="dia"
						type="number"
						placeholder="80"
						required
						bind:value={measure.dia}
						on:change={calculateBloodPressure}
					/>
					<p class=" text-sm text-muted-foreground">mmHg</p>
				</div>
				<div class="grid gap-2">
					<Label for="pulse">PULSE</Label>
					<Input
						id="pulse"
						type="number"
						placeholder="90"
						required
						bind:value={measure.pulse}
						on:change={calculateBloodPressure}
					/>
					<p class=" text-sm text-muted-foreground">bpm</p>
				</div>
			</section>
		{/each}
		<Separator />
	</Card.Content>
	<Card.Footer class="flex w-full flex-col gap-6">
		<section class="flex w-full gap-4">
			<div class="grid w-full gap-2">
				<Label for="sys">SYS</Label>
				<Button class="w-full">{sysAverage}</Button>
				<p class=" text-sm text-muted-foreground">mmHg</p>
			</div>
			<div class="grid w-full gap-2">
				<Label for="dia">DIA</Label>
				<Button class="w-full">{diaAverage}</Button>
				<p class=" text-sm text-muted-foreground">mmHg</p>
			</div>
			<div class="grid w-full gap-2">
				<Label for="pulse">PULSE</Label>
				<Button class="w-full">{pulseAverage}</Button>
				<p class=" text-sm text-muted-foreground">bpm</p>
			</div>
		</section>
	</Card.Footer>
</Card.Root>
