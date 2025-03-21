<template>
    <section class="hero flow section" data-padding="compact">
      <div id="main">
         <div class="employeename">
        <img src="../../assets/imges/GenericAvatar.svg"/>
        <h2> استاذ / طارق المغربى  </h2>
    </div>
<hr>
    <h2 class="target">تارجت</h2>

      </div>
    </section>
</template>
<style>
section {

}
.employeename {
    display: flex;
    align-items: center;
    justify-content: start;
    font-size: 1.5rem;
    gap: 3rem;
    padding-bottom: 1rem;
    font-weight: bold;
    margin-right: 2rem;
    
}

@media (max-width: 768px) {
    .employeename {
    font-size: 1rem;
        gap: 1rem;
    }
}
.target {
    font-size: 1.5rem;
    gap: 2rem;
    padding-bottom: 1rem;
   margin-top: 1rem ;
  font-weight: bold;
}
@media (max-width: 768px) {
    .target{
    font-size: 1.5rem;
        gap: 0.5rem;
    }
}



</style>
