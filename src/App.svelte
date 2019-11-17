<script>
const title = 'Han Variants Quick View';
const empty = '空';

let text = '言葉';
let font = 'sans-serif';

const langs = [
	{ id: 'zh-Hans', name: 'Chinese (simplified)' },
	{ id: 'zh-Hant', name: 'Chinese (traditional)' },
	{ id: 'zh-Hant-HK', name: 'Chinese (traditional, Hong Kong)' },
	{ id: 'ja', name: 'Japanese' },
	{ id: 'ko', name: 'Korean' },
	{ id: 'vi-Hani', name: 'Vietnamese' },
];
</script>

<style>
.header-wrapper, .controls-wrapper {
	font-family: sans-serif;
	margin-left: auto;
	margin-right: auto;
	margin-bottom: 2em;
	max-width: 60ch;
}

.header {
	margin-bottom: 0;
}

.controls-wrapper > * {
	margin-bottom: 1em;
}

.text-input {
	width: 100%;
	font-size: 1.4rem;
}

.font-switcher {
	display: flex;
	align-content: center;
	flex-wrap: wrap;
}

.font-switcher > * {
	margin-right: 1em;
}

.langs {
	display: flex;
	flex-wrap: wrap;
	margin: 0 auto;
	max-width: 100ch;
}

.langs-placeholder-text {
	color: #ccc;
}

.lang {
	flex-grow: 999;
	max-width: 100%;
	padding: 1em;
}

.lang-header {
	text-align: center;
	font-family: sans-serif;
}

.lang-text {
	font-size: 2.25rem;
	text-align: center;
}

.font-serif {
	font-family: serif;
}

.font-sans-serif {
	font-family: sans-serif;
}
</style>

<div class="header-wrapper">
	<h1 class="header">{title}</h1>

	<p>
		<a href="https://en.wikipedia.org/wiki/Han_unification">About Han unification</a>
	</p>
</div>

<div class="controls-wrapper">
	<input class="text-input" type="text" bind:value={text} placeholder="Your CJK text" />

	<div class="font-switcher">
		<label>
			<input type="radio" bind:group={font} value={'sans-serif'}>
			Sans-serif
		</label>
		<label>
			<input type="radio" bind:group={font} value={'serif'}>
			Serif
		</label>
		<label>
			<input type="radio" bind:group={font} value={'default'}>
			Default font
		</label>
	</div>
</div>

<div class="langs {!text && 'langs-placeholder-text'}">
	<div class="lang">
		<div class="lang-header">
			Default variant<br/>
			for your device/browser
		</div>
		<div class="lang-text font-{font}">{text||empty}</div>
	</div>
	{#each langs as lang}
	<div class="lang">
		<div class="lang-header">
			{lang.name}<br/>
			<code>lang="{lang.id}"</code>
		</div>
		<div class="lang-text font-{font}" lang={lang.id}>{text||empty}</div>
	</div>
	{/each}
</div>
