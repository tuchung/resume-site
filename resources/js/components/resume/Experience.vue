<template>
      <sui-segment raised>
        <a is="sui-label" color="yellow" class="profile-ribbon" ribbon>
          Experiences
        </a>
        <div class="paragraph">
           <h2 class="sui-header company">Agency Matrix: 2015-2018</h2>
           <h4 class="sui-header role">Full-Stack Developer</h4>
           <p>Responsibility Included:</p>
           <sui-list bulleted>
                <sui-list-item>Developing and Maintenance Agency Matrix's insurance management system.</sui-list-item>
                <sui-list-item>Lead Developer / Co-Creator of Benefit Matrix, its core and all of its extensions.</sui-list-item>
                <sui-list-item>Lead Developer of the largely anticipated Commercial overhaul of the System.</sui-list-item>
            </sui-list>
        </div>


      </sui-segment>

</template>

<script>
export default {
    Name: 'Experience'
};
</script>

<style scoped>
    .profile-ribbon{
        font-size: 20px;
    }

    .paragraph{
        margin-top: 10px;
    }

    .company{
        color:lightskyblue;
    }

    .role{
        color: lightgrey;
    }
</style>

