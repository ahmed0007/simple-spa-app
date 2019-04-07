<template>

	<div>

	
		

		<div class="image__preview">

			<img 

			

			v-if="image"

			style="
					height: 150px;
						
						width: 150px;

						border-radius: 3px;"


			:src="image">

			<a class="btn btn-danger preview-cancel" v-if="preview" 

			

				@click="close"
				
				>
				
				<i class="far fa-window-close"></i>

			</a>
			

		</div>

		

		

	

		


	
		

	</div>
	
	

	


</template>


<script type="text/javascript">
	
	export default {

		props:{

			preview:{

				type: [String, File],

				default: null

			}


		},

		data(){


			return {

				image: 'default-avatar.png'

			};

		},

		created(){

			this.setPreview();

		},

		watch:{

			'preview': 'setPreview'

		},
 

		methods:{


			setPreview(){

                    if(this.preview){

                        this.image = this.preview;

                    }


				

			},

			close(){

				this.preview = null	
				this.image = 'default-avatar.png';

				this.$emit('close')

			}


		}


	}


</script>


<style type="text/css">

.image__preview{

    position: relative;

}
	
.preview-cancel{

	position: absolute;
	
	padding: 0px;

	/* top: -10px; */
	top: 0px;

	right: 0;

	border-radius: 0px;



}


</style>