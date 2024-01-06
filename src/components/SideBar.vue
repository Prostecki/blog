<template>
  <!-- Sidebar component -->
  <aside :style="{ transform: 'translateX(' + (sidebarOpen ? '0px' : '-300px') + ')' }" class="sidebar">
    <!-- Close button for the sidebar -->
    <button type="button" @click="closeSidebarHandler">X</button>
    <!-- Author's name -->
    <h1>{{ author }}</h1>
    <!-- Message in the sidebar -->
    <p>{{ message }}</p>
    
    <!-- Additional information in the sidebar -->
    <div class="sidebar-section">
      <h2>Contact Information</h2>
      <ul>
        <li>Email: {{ contact.email }}</li>
        <li>Twitter: <a :href="contact.twitter" target="_blank">{{ contact.twitterHandle }}</a></li>
      </ul>
    </div>

    <!-- Any other dynamic content or data you want to display -->
  </aside>
</template>

<script>
export default {
  // Component name
  name: "SideBar",
  // Props for receiving data from the parent component
  props: {
    sidebarOpen: Boolean, // Boolean prop indicating if the sidebar is open
    closeSidebar: Function, // Function prop to close the sidebar
  },
  // Methods for handling actions in the component
  methods: {
    // Method to handle closing the sidebar
    closeSidebarHandler() {
      console.log('Closed'); // Log message when sidebar is closed
      this.closeSidebar(); // Call the provided closeSidebar function
    },
  },
  // Data properties for storing component-specific data
  data() {
    return {
      author: "Prostecki", // Author's name
      message: "Hey everyone!", // Message in the sidebar
      contact: {
        email: "prostecki@example.com",
        twitterHandle: "@prostecki",
        twitter: "https://twitter.com/prostecki",
      },
      // Any other data you want to include in the sidebar
    };
  },
};
</script>

<style scoped>
  /* Styling for the sidebar */
  .sidebar {
    text-align: left;
    width: 250px;
    height: 100%;
    background-color: #fff;
    color: #14171a;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    position: fixed;
    z-index: 5;
    top: 0;
    border-right: 2px solid #e1e8ed;
    transition: transform 0.4s ease;
  }
  .sidebar-open {
    left: 0;
  }
  /* Styling for the close button */
  button {
    position: absolute;
    top: 10px;
    right: 10px;
    width: 30px;
    height: 30px;
    font-size: 16px;
    font-weight: bold;
    background: none;
    border: none;
    cursor: pointer;
    transition: background-color 0.4s, color 0.4s;
  }
  /* Styling for the close button on hover */
  button:hover {
    background-color: #e1e8ed; /* Twitter's button hover color */
    color: #1da1f2; /* Twitter's blue color */
  }
  /* Styling for additional sections inside the sidebar */
  .sidebar-section {
    margin-top: 20px;
    border-top: 1px solid #e1e8ed;
    padding-top: 20px;
  }
  .sidebar-section h2 {
    font-size: 18px;
    margin-bottom: 10px;
  }
  .sidebar-section ul {
    list-style: none;
    padding: 0;
  }
  .sidebar-section li {
    margin-bottom: 10px;
  }
</style>
