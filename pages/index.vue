<template>
  <div>
    <MeCard />

    <NuxtContent :document="index" class="max-w-none prose" />

    <Section title="Projects">
      <p>Some of the interesting things that I have built/contributed to.</p>
      <ProjectList />
    </Section>

    <Section title="Education">
      <ul>
        <li>
          B. Tech. (Honors) in
          <a
            href="https://cse.iith.ac.in"
            class="text-primary underline dark:text-blue-300 hover:no-underline"
            >Computer Science and Engineering</a
          >, 2015 - 2019
          <br />
          <a
            href="https://iith.ac.in"
            class="text-primary underline dark:text-blue-300 hover:no-underline"
            >Indian Institute of Technology Hyderabad</a
          >
        </li>
      </ul>
    </Section>

    <Section title="Publications">
      <PublicationList />
      <a
        href="https://scholar.google.co.in/citations?user=M1NFyhAAAAAJ&hl=en"
        :class="[
          'bg-primary',
          'text-white',
          'border-primary',
          'border',
          'inline-block',
          'rounded',
          'py-1',
          'px-3',
          'mt-4',
          'hover:bg-white',
          'hover:text-primary',
          'dark:bg-blue-300',
          'dark:text-primary',
          'dark:border-blue-300',
          'dark:hover:bg-primary',
          'dark:hover:text-white',
        ]"
        >Google Scholar</a
      >
    </Section>

    <Section title="Contact">
      <div class="buttons">
        <a
          href="mailto:prateek@prateekkumar.in"
          class="text-primary dark:text-blue-300"
        >
          <span class="icon pr-2">
            <font-awesome :icon="['fas', 'envelope']" />
          </span>
          <span class="underline hover:no-underline"
            >prateek@prateekkumar.in</span
          >
        </a>
      </div>
    </Section>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import MeCard from '~/components/MeCard.vue';
import PublicationList from '~/components/home/PublicationList.vue';
import ProjectList from '~/components/home/ProjectList.vue';
import Section from '~/components/home/Section.vue';

export default Vue.extend({
  components: {
    MeCard,
    Section,
    PublicationList,
    ProjectList,
  },
  async asyncData({ $content }) {
    const index = await $content('index').fetch();
    return { index };
  },
  head: {
    script: [
      {
        innerHTML: JSON.stringify(
          {
            '@context': 'https://schema.org',
            '@type': 'Person',
            email: 'prateek@prateekkumar.in',
            name: 'Prateek Kumar',
            gender: 'male',
            image: 'https://prateekkumar.in/images/profile.jpg',
            url: 'https://prateekkumar.in',
            sameAs: [
              'https://twitter.com/prateekkumarweb',
              'https://github.com/prateekkumarweb',
              'https://www.linkedin.com/in/prateekkumarweb',
            ],
            alumniOf: [
              {
                '@type': 'CollegeOrUniversity',
                name: 'Indian Institute of Technology Hyderabad',
                url: 'https://iith.ac.in',
              },
            ],
          },
          null,
          2
        ),
        type: 'application/ld+json',
      },
    ],
    __dangerouslyDisableSanitizers: ['script'], // required because vue-meta escapes " as &quot;
  },
});
</script>
