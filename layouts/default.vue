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
          <LinksNavLink to="/">Accueil</LinksNavLink>
          <LinksNavLink to="/produit">Produits</LinksNavLink>
          <LinksNavLink to="/societe"> Société </LinksNavLink>
          <LinksNavLink to="/equipe"> Equipe </LinksNavLink>
          <LinksNavLink to="/contact"> Contact </LinksNavLink>
          <LinksNavLink to="/blog"> Blog </LinksNavLink>


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
