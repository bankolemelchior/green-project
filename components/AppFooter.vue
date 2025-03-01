<script setup lang="ts">
const toast = useToast();
function subscribeToNewsletter() {
    toast.add({
        title: 'Souscription réussie',
        description: 'Merci pour votre inscription à notre newsletter.',
        icon: 'simple-icons:maildotru',
        // color: 'success'
    });
}
    const links = [
  {
    label: 'Resources',
    children: [
      {label: 'Documentation'},
      {label: 'Starter Kits'},
      {label: 'Release Notes'},
      {label: 'Blog'},
      {label: 'Partners'},
      {label: 'News'},
      {label: 'Larabelles'},
      {label: 'Jobs'},
      {label: 'Careers'},
    ]
  }, 
  {
    label: 'Products',
    children: [
      {label: 'Cloud'},
      {label: 'Forge'},
      {label: 'Nighwatch'},
      {label: 'Nova'},
    ],
  }, 
  {
    label: 'Packages',
    children: [
      {label: 'Cashier'},
      {label: 'Dusk'},
      {label: 'Hrizon'},
      {label: 'Octane'},
      {label: 'Scout'},
      {label: 'Pennant'},
      {label: 'Pint'},
    ],
  }
];

</script>

<template>
    <div>
        <UDivider icon="simple-icons:nuxtdotjs"/>
        <UContainer >
            <UFooter >
                <template #top>
                    <UFooterColumns :links="links" >
                        <!-- <template #left>
                            <UFooterLinks :links="links" />
                        </template> -->
                        <template #right>                          
                            <form @submit.prevent="subscribeToNewsletter">
                            <UFormGroup 
                                label="Souscrire à notre newsletter"
                                description="Recevez les dernières nouvelles de notre blog directement dans votre boîte de réception."
                                required
                                >
                                <UInput
                                    type="email"
                                    placeholder="Votre email"
                                    icon="simple-icons:maildotru"
                                >
                                <template #trailing>
                                    <UButton type="submit" variant="solid" color="primary">Souscrire </UButton>
                                </template>
                            </UInput>
                            </UFormGroup>
                        </form>
                        </template>
                    </UFooterColumns>

                </template>

                <template #left>
                    <p>
                        &copy; {{ new Date().getFullYear() }}
                        <span>&middot;</span>Connecty
                    </p>
                </template>

                <template #right>
                    <UColorModeButton />
                </template>
            </UFooter>
        </UContainer>
    </div>
</template>

<style scoped></style>