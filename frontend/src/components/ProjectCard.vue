<script>
export default {
	props: {
		project: { type: Object, required: true },
	},
	el: '#container',

  methods: {
    copy() {
      try {
        navigator.clipboard.writeText(this.project.link);
		alert('Bạn đã copy thành công link phim '+ this.project.name);
      } catch (e) {
        throw e
      }
    }
  },
};

</script>

<template>
	<div class="card text-white bg-dark" style="width: 30rem;">
		<div class="card-body">
  
			<div class="p-1">
				<strong class="card-text text-warning">Tên phim:</strong>
				{{ project.name }}
			</div>
			<div class="p-1">
				<strong class="card-text text-warning">Mô tả phim:</strong>
				{{ project.decripsion }}
			</div>
			<div class="p-1">
				<strong class="card-text text-warning">Địa chỉ phim:</strong><br>
				{{ project.link }} 

				
			</div>
	
			<div class="p-1">
				<strong class="card-text text-warning">Phim yêu thích:&nbsp;</strong>
				<i v-if="project.favorite" class="fas fa-check"></i>
				<i v-else class="fas fa-times"></i>
			</div>
			<div class="p-1">
				<button class="btn btn-info" @click="copy" style="border-radius: 5px; float: right;  font-weight: bold;">Copy link</button>
			</div>
			
		</div>
	</div>
</template>
