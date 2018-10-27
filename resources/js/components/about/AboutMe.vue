<template>
    <sui-segment raised>
        <h2 class="sui-header">About Me</h2>
        <div class="paragraph">
            <sui-grid celled class="column-content">
                <sui-grid-row>
                <sui-grid-column :width="3">
                    <img  :src="'images/profile.png'"/>
                </sui-grid-column>
                <sui-grid-column :width="13">
                <h3>
                  I am of vietnamese/chinese descendent. I came to the United States when I was ten years old.
                I attended and graduated from Georgia Gwinnett College in 2015. While I was there I worked for the college
                as a technical support specialist for 2 years. Right out of school, I was hired to work as a full stack junior
                software developer for Agency Matrix, an insurance management software company. One year later, I was promoted to
                lead developer and were given a software extension to build, this later became the company benefit department and has grown
                greatly in size. A year afterward, I was leading an internal team of three developer including myself. together
                we continue to develop the benefit system and at the same time implementing the commerical overhaul of Agency Matrix. In addition,
                I was nominated for Amazing Accomplishment in 2017 by WORK SOURCE GEORGIA.
                  </h3>
                </sui-grid-column>
                </sui-grid-row>
            </sui-grid>

        </div>

      </sui-segment>
</template>

<script>

export default {
    Name: 'AboutMe',
};
</script>

<style scoped>
    .column-content{
        margin: 10px;
    }
</style>

