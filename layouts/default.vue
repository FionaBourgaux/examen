<template>
  <Head>
    <Title>Paws & Play VR</Title>
    <Meta name="description" content="Bienvenue sur la société fictive de Paws & Play VR" />

    <Meta
      property="og:description"
      content="Découverte Interactive de Paws & Play VR "
    />

    <Meta
      property="og:url"
      content="https://examen-fionabourgaux.vercel.app/"
    />
    <Meta property="og:type" content="website" />
    <Meta property="og:locale" content="fr_FR" />
    <Meta property="og:site_name" content="Société fictive" />
    <Meta name="theme-color" content="#FFFFF" />
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
