<template>
  <Head>
    <Title>Design System</Title>
    <Meta name="description" content="Paws & Play VR" />
  </Head>
  <LayoutsBase>
    <template #navigation>
      <NavsNav>
        <template #logo>
          <TitresLogo> 
             <NuxtImg
            class="h-16 w-16"
        src="/images/logo.jpeg"
        alt="logo"
      />
            <div> Paws & Play VR</div>

           
          </TitresLogo>
        </template>

        <template #links>
          <div id="#accueil">
          <LinksNavLink to="/">Accueil</LinksNavLink>
          </div>

          <div id="#produit">
          <LinksNavLink to="/produit">Produits</LinksNavLink></div>
          
          <div id="#societe">
          <LinksNavLink to="/societe"> Société </LinksNavLink></div>
          
          <div id="#equipe">
          <LinksNavLink to="/equipe"> Équipe </LinksNavLink> </div>

           <div id="#contact">
          <LinksNavLink to="/contact"> Contact </LinksNavLink></div>

          <div id="#blog">
          <LinksNavLink to="/blog"> Blog </LinksNavLink></div>


        </template>
      </NavsNav>
    </template>

    <template #content>
      <slot />
    </template>

    <template #footer>
      <FootersBasic />
    </template>
  </LayoutsBase>
</template>
