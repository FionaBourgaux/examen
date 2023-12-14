<template>
  <Head>
    <Title>Design System</Title>
    <Meta name="description" content="Paws & Play VR" />
  </Head>
  <LayoutsBase>
    <template #navigation>
      <NavsNav>
        <template #logo>
          <TitresLogo>Paws & Play VR</TitresLogo>
        </template>

        <template #links>
          <LinksNavLink to="/">Accueil</LinksNavLink>
          <LinksNavLink to="/docs">Produits</LinksNavLink>
          <LinksNavLink to="/docs"> Société </LinksNavLink>
          <LinksNavLink to="/docs"> Equipe </LinksNavLink>
          <LinksNavLink to="/docs"> Contact </LinksNavLink>
          <LinksNavLink to="/docs"> Blog </LinksNavLink>


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
