<template>
  <main id="main-content">
    <section class="hp-intro">
      <div class="hp-intro__content">
        <h1>Brain Covid</h1>
        <p class="hp-intro__subtitle">
          Data sharing and collaboration initiative
        </p>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi natus
          ratione laudantium, impedit, itaque enim consectetur deserunt ab
          assumenda fugit molestias numquam repudiandae in autem dignissimos
          mollitia, sunt optio a!
        </p>
        <div class="hp-intro__links">
          <nuxt-link class="button" to="/mri/">MRI data</nuxt-link>
          <nuxt-link class="button" to="/histology/">Histology data</nuxt-link>
          <nuxt-link class="" to="#about"
            >Learn more about this projet</nuxt-link
          >
        </div>
      </div>
      <div class="hp-intro__image">
        <nuxt-picture
          class="hp-intro__image"
          src="/homepage/human-brain-color.png"
          sizes="sm:100vw xl:400px"
          alt=""
          width="400"
          height="500"
        />
      </div>
    </section>
    <section>
      <article id="about" class="editorial">
        <h1>About this project</h1>
        <p>
          COVID-19 is a major public health problem that has affected almost the
          entire planet, causing 12 million cases and more than 550 000 deaths
          (Public Health France).
        </p>
        <p>
          Check out our <nuxt-link to="#members">members</nuxt-link> and
          <nuxt-link to="#partners">partners</nuxt-link>
        </p>
        <h2>Genesis</h2>
        <p>
          If most deaths are due to respiratory or cardiovascular failure, it
          quickly became apparent during the epidemic that the virus had a
          tropism for the central nervous system (Ellul et al. 2020). The
          nervous impairment seems to take many forms and its mechanisms,
          undoubtedly multiple, are being explored. Certain signs and symptoms
          plead for a direct viral attack of the nervous system: anosmia,
          meningitis and temporal necrotizing encephalitis resembling that of
          herpes (Moriguchi et al. 2020, Poyiadji et al. 2020).
        </p>
        <p>
          The detection of viral particles in the endothelium of the brain
          vessels argues for this direct role of the virus (Paniz-Mondolfi et
          al. 2020) and could explain the occurrence of strokes in young people
          (Oxley et al. 2020). Neuropathological studies are still few.
        </p>
        <p>
          Relatively few autopsied cases and the lesions observed offer few
          arguments for direct action by the virus (Solomon et al. 2020). Ante-
          and post-mortem MRI imaging studies have reported multiple lesions
          associated with micro- spotting (Coolen et al. 2020). The hypothesis
          of secondary immune encephalitis has been raised in the face of
          multiple lesions of the white matter suggestive of ADEM (Reichard et
          al. 2020).
        </p>
        <p>
          Using postmortem MRI, subcortical micro and macro bleeds were reported
          (Coolen et al. 2020). Here, we propose a study combining ex vivo
          imaging by MRI and neuropathological study to elucidate the nature of
          the lesions observed in COVID + patients, their specificity, their
          pathophysiology whether it is directly linked to viral replication or
          secondary to the infection. Our study aims to link ex-vivo brain MRI
          signal abnormalities with neuropathological findings relative to the
          SARS-CoV-2 infection.
        </p>
        <h2>Methods</h2>
        <p>
          MRI offers a “big picture” image on the whole organ compared to
          conventional histology, which is often limited to small sections. Here
          we will combine available techniques developed at both Institutes
          (Institut Pasteur and Paris Brain Institute - ICM) to facilitate the
          comparison and the characterisation of brain lesions linked to the
          viral infection.
        </p>
        <p>
          Our project should produce a new description of the anatomical
          structures affected by the infection in the central nervous system,
          and in particular those related to the brain vascular system.
        </p>
        <p>
          Eight brains from COVID-19 patients will be studied and compared to
          matched controls. Autopsies will be performed according to the current
          procedure for interrogating the national refusal register (RNR),
          combined with the collection of testimonies from relatives on the
          wishes of the deceased and their information on the use of samples for
          research.
        </p>
        <p>
          Sampling and storing will be done following the COVITIS protocol,
          approved by the authorized institutions (Agence de la Biomédecine PFS
          20-008; French ministry of research DC2020- 4022).
        </p>

        <section>
          <h2 id="members">Members</h2>
          <ul class="members__list" clean-list>
            <li v-for="member of members" :key="member.id">
              <member-card :member="member" />
            </li>
          </ul>
        </section>

        <section>
          <h2 id="partners">Partners</h2>
          <ul class="partners__list" clean-list>
            <li class="partner">
              <!-- using nuxt-picture for jpg/png -->
              <nuxt-picture
                src="/partners/icm-logo.png"
                width="200"
                height="214"
                loading="lazy"
              />
            </li>
            <li class="partner">
              <!-- using nuxt-img for svg -->
              <nuxt-img
                src="/partners/Logo-Institut_Pasteur.svg"
                width="200"
                height="54"
                loading="lazy"
              />
            </li>
          </ul>
        </section>
      </article>
    </section>
  </main>
</template>

<script>
export default {
  // fetch members from '/content/members'
  async asyncData({ $content, error }) {
    const members = await $content('members')
      .sortBy('createdAt', 'asc')
      .fetch()
      .catch((err) => {
        error({ statusCode: 404, message: 'Page not found' })
        console.log(err)
      })

    return {
      members,
    }
  },
}
</script>

<style scoped>
.hp-intro {
  margin: 4rem auto 2rem;
  max-width: 120rem;
  display: grid;
  grid-template-columns: 1fr;
  align-items: center;
  justify-content: space-between;
  gap: 6rem;
}
.hp-intro h1 {
  margin: 0;
}
.hp-intro__subtitle {
  font-size: clamp(2.6rem, 2.4rem + 0.625vw, 3.2rem);
  font-weight: 300;
}
.hp-intro__links {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.hp-intro__links > * {
  margin: 0;
}
.hp-intro__links > * + * {
  margin-top: 1.6rem;
}
.hp-intro__image {
  position: relative;
  justify-self: center;
}
/* About */
.members__list,
.partners__list {
  margin-top: 3rem;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(240px, 100%), 1fr));
  gap: 3rem;
}
.partners__list {
  align-items: center;
}
.partner {
  padding: 2rem;
  height: 100%;
  display: flex;
  place-content: center;
  border-radius: 8px;
  background-color: var(--contrast);
}

@media screen and (min-width: 1024px) {
  .hp-intro {
    /* header height and margins */
    min-height: calc(100vh - 7.6rem - 6rem);
    grid-template-columns: 3fr 2fr;
  }
}
</style>
