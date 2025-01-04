<script>
  import Footer from "./lib/components/Footer.svelte";
  import Header from "./lib/components/Header.svelte";
  import MenuBar from "./lib/components/MenuBar.svelte";
  import Tab from "./lib/components/Tab.svelte";
  import ContactContent from "./lib/pages/ContactContent.svelte";
  import HomeContent from "./lib/pages/HomeContent.svelte";
  import ProjectsContent from "./lib/pages/ProjectsContent.svelte";
  import SkillsContent from "./lib/pages/SkillsContent.svelte";

  let activeTab = "home";

  const tabs = [
    { id: "home", name: "inicio.txt" },
    { id: "projects", name: "proyectos.txt" },
    { id: "skills", name: "habilidades.txt" },
    { id: "contact", name: "contacto.txt" },
  ];
</script>

<div class="min-h-screen bg-white">
  <Header />
  <div class="bg-white rounded">
    <div class="flex gap-1 overflow-x-auto scrollbar-hide py-1">
      <span class="text-xl mx-3">🐄</span>
      {#each tabs as tab}
        <Tab
          name={tab.name}
          isActive={activeTab === tab.id}
          on:click={() => (activeTab = tab.id)}
        />
      {/each}
    </div>
    <MenuBar />
    <main class="p-4 mb-10 overflow-x-auto scrollbar-hide">
      {#if activeTab === "projects"}
        <ProjectsContent />
      {:else if activeTab === "skills"}
        <SkillsContent />
      {:else if activeTab === "contact"}
        <ContactContent />
      {:else}
        <HomeContent />
      {/if}
    </main>
  </div>
  <Footer />
</div>
