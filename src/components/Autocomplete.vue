<template src="./Autocomplete.html">
</template>

<script>
export default {
	name: 'SearchAutocomplete',
	props: {
		cities: {
			type: Array,
			required: false,
			default: () => [],
		},
		books: {
			type: Array,
			required: false,
			default: () => [],
		},
	},
	data() {
		return {
			isOpen: false,
			citySearch: true,
			results: [],
			noResults: false,
			search: "",
			arrowCounter: 0,
		};
	},
	watch: {
		cities: function (value, oldValue) {
			if (value.length !== oldValue.length) {
				this.results = value;
			}
		},
		books: function (value, oldValue) {
			if (value.length !== oldValue.length) {
				this.results = value;
			}
		},
	},
	mounted() {
		document.addEventListener('click', this.handleClickOutside),
		this.focusInput();
	},
	unmounted() {
		document.removeEventListener('click', this.handleClickOutside)
	},
	methods: {
		focusInput() {
			this.$refs.search.focus();
		},
		onChange() {
			this.$emit('input', this.search);
			if (this.search.length > 2) {
				this.filterResults();
				this.isOpen = true;
				if (this.results.length === 0) {
					this.noResults = true;
				} else {
					this.noResults = false;
				}
			} else {
				this.isOpen = false;
			}
		},
		filterResults() {
			if (this.citySearch) {
				this.results = this.cities.filter(city => {
					return city.toLowerCase().indexOf(this.search.toLowerCase()) > -1;
				});
			} else {
				this.results = this.books.filter(book => {
					return book.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1;
				});
			}
		},
		setResult(result) {
			this.search = (this.citySearch ? result : result.title);
			this.isOpen = false;
		},
		changeSearch() {
			this.isOpen = false;
			this.citySearch = !this.citySearch;
		},
		handleClickOutside(event) {
			if (!this.$el.contains(event.target)) {
				this.isOpen = false;
				this.arrowCounter = -1;
			}
		},
		onArrowDown() {
			if (this.arrowCounter < this.results.length) {
				this.arrowCounter = this.arrowCounter + 1;
			}
		},
		onArrowUp() {
			if (this.arrowCounter > 0) {
				this.arrowCounter = this.arrowCounter - 1;
			}
		},
		onEnter() {
			this.search = this.results[this.arrowCounter];
			this.isOpen = false;
			this.arrowCounter = -1;
		},
	},
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
@import './Autocomplete.scss';
</style>
