<template>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
         <div class="employeename">
        <img src="../../assets/imges/GenericAvatar.svg"/>
        <div><h2> استاذ / طارق المغربى  </h2></div>
    </div>

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
    justify-content: center;
    font-size: 1.5rem;
    gap: 2rem;
    padding-bottom: 1rem;
    border-bottom: 2px  #D9D9D9 solid;
    font-weight: bold;
}

@media (max-width: 768px) {
    .employeename {
    font-size: 1rem;
        gap: 0.5rem;
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
