<template>
  <div class="p-grid p-fluid">
    <div class="p-col-12">
      <div class="card card-w-title">
        <h5>Menubar</h5>
        <Menubar :model="nestedMenuitems">
          <template #end>
            <span class="p-input-icon-left">
              <i class="pi pi-search" />
              <InputText type="text" placeholder="Search" />
            </span>
          </template>
        </Menubar>
      </div>
    </div>

    <div class="p-col-12">
      <div class="card card-w-title">
        <h5>Breadcrumb</h5>
        <Breadcrumb :home="breadcrumbHome" :model="breadcrumbItems" />
      </div>
    </div>

    <div class="p-col-12 p-md-6">
      <div class="card card-w-title">
        <h5>Steps</h5>
        <p>Steps and TabMenu are integrated with the same child routes.</p>
        <Steps :model="nestedRouteItems" :readonly="false" />
        <router-view />
      </div>
    </div>

    <div class="p-col-12 p-md-6">
      <div class="card card-w-title">
        <h5>TabMenu</h5>
        <p>Steps and TabMenu are integrated with the same child routes.</p>
        <TabMenu :model="nestedRouteItems" />
        <router-view />
      </div>
    </div>

    <div class="p-col-12 p-md-4">
      <div class="card">
        <h5>Tiered Menu</h5>
        <TieredMenu :model="tieredMenuItems" />
      </div>
    </div>

    <div class="p-col-12 p-md-4">
      <div class="card">
        <h5>Plain Menu</h5>
        <Menu :model="menuitems" />
      </div>
    </div>

    <div class="p-col-12 p-md-4">
      <div class="card">
        <h5>Overlay Menu</h5>

        <Menu ref="menu" :model="overlayMenuItems" :popup="true" />
        <Button
          type="button"
          label="Options"
          icon="pi pi-angle-down"
          @click="toggleMenu"
          style="width: auto"
        />
      </div>

      <div class="card" @contextmenu="onContextRightClick">
        <h5>ContextMenu</h5>
        Right click to display.
        <ContextMenu ref="contextMenu" :model="contextMenuItems" />
      </div>
    </div>

    <div class="p-col-12 p-md-6">
      <div class="card">
        <h5>MegaMenu - Horizontal</h5>
        <MegaMenu :model="megamenuItems" />

        <h5 style="margin-top: 1.55em">MegaMenu - Vertical</h5>
        <MegaMenu :model="megamenuItems" orientation="vertical" />
      </div>
    </div>

    <div class="p-col-12 p-md-6">
      <div class="card">
        <h5>PanelMenu</h5>
        <PanelMenu :model="panelMenuitems" />
      </div>
    </div>
  </div>
</template>

<script>
import Layout from "../../layout/App";
export default {
  layout: Layout,
  data() {
    return {
      nestedMenuitems: [
        {
          label: "Customers",
          icon: "pi pi-fw pi-table",
          items: [
            {
              label: "New",
              icon: "pi pi-fw pi-user-plus",
              items: [
                {
                  label: "Customer",
                  icon: "pi pi-fw pi-plus",
                },
                {
                  label: "Duplicate",
                  icon: "pi pi-fw pi-copy",
                },
              ],
            },
            {
              label: "Edit",
              icon: "pi pi-fw pi-user-edit",
            },
          ],
        },
        {
          label: "Orders",
          icon: "pi pi-fw pi-shopping-cart",
          items: [
            {
              label: "View",
              icon: "pi pi-fw pi-list",
            },
            {
              label: "Search",
              icon: "pi pi-fw pi-search",
            },
          ],
        },
        {
          label: "Shipments",
          icon: "pi pi-fw pi-envelope",
          items: [
            {
              label: "Tracker",
              icon: "pi pi-fw pi-compass",
            },
            {
              label: "Map",
              icon: "pi pi-fw pi-map-marker",
            },
            {
              label: "Manage",
              icon: "pi pi-fw pi-pencil",
            },
          ],
        },
        {
          label: "Profile",
          icon: "pi pi-fw pi-user",
          items: [
            {
              label: "Settings",
              icon: "pi pi-fw pi-cog",
            },
            {
              label: "Billing",
              icon: "pi pi-fw pi-file",
            },
          ],
        },
        {
          label: "Quit",
          icon: "pi pi-fw pi-sign-out",
        },
      ],
      breadcrumbHome: { icon: "pi pi-home", to: "/" },
      breadcrumbItems: [
        { label: "Computer" },
        { label: "Notebook" },
        { label: "Accessories" },
        { label: "Backpacks" },
        { label: "Item" },
      ],
      nestedRouteItems: [
        {
          label: "Personal",
          to: "/menu",
        },
        {
          label: "Seat",
          to: "/menu/seat",
        },
        {
          label: "Payment",
          to: "/menu/payment",
        },
        {
          label: "Confirmation",
          to: "/menu/confirmation",
        },
      ],
      tieredMenuItems: [
        {
          label: "Customers",
          icon: "pi pi-fw pi-table",
          items: [
            {
              label: "New",
              icon: "pi pi-fw pi-user-plus",
              items: [
                {
                  label: "Customer",
                  icon: "pi pi-fw pi-plus",
                },
                {
                  label: "Duplicate",
                  icon: "pi pi-fw pi-copy",
                },
              ],
            },
            {
              label: "Edit",
              icon: "pi pi-fw pi-user-edit",
            },
          ],
        },
        {
          label: "Orders",
          icon: "pi pi-fw pi-shopping-cart",
          items: [
            {
              label: "View",
              icon: "pi pi-fw pi-list",
            },
            {
              label: "Search",
              icon: "pi pi-fw pi-search",
            },
          ],
        },
        {
          label: "Shipments",
          icon: "pi pi-fw pi-envelope",
          items: [
            {
              label: "Tracker",
              icon: "pi pi-fw pi-compass",
            },
            {
              label: "Map",
              icon: "pi pi-fw pi-map-marker",
            },
            {
              label: "Manage",
              icon: "pi pi-fw pi-pencil",
            },
          ],
        },
        {
          label: "Profile",
          icon: "pi pi-fw pi-user",
          items: [
            {
              label: "Settings",
              icon: "pi pi-fw pi-cog",
            },
            {
              label: "Billing",
              icon: "pi pi-fw pi-file",
            },
          ],
        },
        {
          separator: true,
        },
        {
          label: "Quit",
          icon: "pi pi-fw pi-sign-out",
        },
      ],
      overlayMenuItems: [
        {
          label: "Save",
          icon: "pi pi-save",
        },
        {
          label: "Update",
          icon: "pi pi-refresh",
        },
        {
          label: "Delete",
          icon: "pi pi-trash",
        },
        {
          separator: true,
        },
        {
          label: "Home",
          icon: "pi pi-home",
        },
      ],
      menuitems: [
        {
          label: "Customers",
          items: [
            {
              label: "New",
              icon: "pi pi-fw pi-plus",
            },
            {
              label: "Edit",
              icon: "pi pi-fw pi-user-edit",
            },
          ],
        },
        {
          label: "Orders",
          items: [
            {
              label: "View",
              icon: "pi pi-fw pi-list",
            },
            {
              label: "Search",
              icon: "pi pi-fw pi-search",
            },
          ],
        },
      ],
      contextMenuItems: [
        {
          label: "Save",
          icon: "pi pi-save",
        },
        {
          label: "Update",
          icon: "pi pi-refresh",
        },
        {
          label: "Delete",
          icon: "pi pi-trash",
        },
        {
          separator: true,
        },
        {
          label: "Options",
          icon: "pi pi-cog",
        },
      ],
      megamenuItems: [
        {
          label: "Fashion",
          icon: "pi pi-fw pi-tag",
          items: [
            [
              {
                label: "Woman",
                items: [
                  { label: "Woman Item" },
                  { label: "Woman Item" },
                  { label: "Woman Item" },
                ],
              },
              {
                label: "Men",
                items: [
                  { label: "Men Item" },
                  { label: "Men Item" },
                  { label: "Men Item" },
                ],
              },
            ],
            [
              {
                label: "Kids",
                items: [{ label: "Kids Item" }, { label: "Kids Item" }],
              },
              {
                label: "Luggage",
                items: [
                  { label: "Luggage Item" },
                  { label: "Luggage Item" },
                  { label: "Luggage Item" },
                ],
              },
            ],
          ],
        },
        {
          label: "Electronics",
          icon: "pi pi-fw pi-desktop",
          items: [
            [
              {
                label: "Computer",
                items: [{ label: "Computer Item" }, { label: "Computer Item" }],
              },
              {
                label: "Camcorder",
                items: [
                  { label: "Camcorder Item" },
                  { label: "Camcorder Item" },
                  { label: "Camcorder Item" },
                ],
              },
            ],
            [
              {
                label: "TV",
                items: [{ label: "TV Item" }, { label: "TV Item" }],
              },
              {
                label: "Audio",
                items: [
                  { label: "Audio Item" },
                  { label: "Audio Item" },
                  { label: "Audio Item" },
                ],
              },
            ],
            [
              {
                label: "Sports.7",
                items: [{ label: "Sports.7.1" }, { label: "Sports.7.2" }],
              },
            ],
          ],
        },
        {
          label: "Furniture",
          icon: "pi pi-fw pi-image",
          items: [
            [
              {
                label: "Living Room",
                items: [
                  { label: "Living Room Item" },
                  { label: "Living Room Item" },
                ],
              },
              {
                label: "Kitchen",
                items: [
                  { label: "Kitchen Item" },
                  { label: "Kitchen Item" },
                  { label: "Kitchen Item" },
                ],
              },
            ],
            [
              {
                label: "Bedroom",
                items: [{ label: "Bedroom Item" }, { label: "Bedroom Item" }],
              },
              {
                label: "Outdoor",
                items: [
                  { label: "Outdoor Item" },
                  { label: "Outdoor Item" },
                  { label: "Outdoor Item" },
                ],
              },
            ],
          ],
        },
        {
          label: "Sports",
          icon: "pi pi-fw pi-star-o",
          items: [
            [
              {
                label: "Basketball",
                items: [
                  { label: "Basketball Item" },
                  { label: "Basketball Item" },
                ],
              },
              {
                label: "Football",
                items: [
                  { label: "Football Item" },
                  { label: "Football Item" },
                  { label: "Football Item" },
                ],
              },
            ],
            [
              {
                label: "Tennis",
                items: [{ label: "Tennis Item" }, { label: "Tennis Item" }],
              },
            ],
          ],
        },
      ],
      panelMenuitems: [
        {
          label: "Customers",
          icon: "pi pi-fw pi-table",
          items: [
            {
              label: "New",
              icon: "pi pi-fw pi-user-plus",
              items: [
                {
                  label: "Customer",
                  icon: "pi pi-fw pi-plus",
                },
                {
                  label: "Duplicate",
                  icon: "pi pi-fw pi-copy",
                },
              ],
            },
            {
              label: "Edit",
              icon: "pi pi-fw pi-user-edit",
            },
          ],
        },
        {
          label: "Orders",
          icon: "pi pi-fw pi-shopping-cart",
          items: [
            {
              label: "View",
              icon: "pi pi-fw pi-list",
            },
            {
              label: "Search",
              icon: "pi pi-fw pi-search",
            },
          ],
        },
        {
          label: "Shipments",
          icon: "pi pi-fw pi-envelope",
          items: [
            {
              label: "Tracker",
              icon: "pi pi-fw pi-compass",
            },
            {
              label: "Map",
              icon: "pi pi-fw pi-map-marker",
            },
            {
              label: "Manage",
              icon: "pi pi-fw pi-pencil",
            },
          ],
        },
        {
          label: "Profile",
          icon: "pi pi-fw pi-user",
          items: [
            {
              label: "Settings",
              icon: "pi pi-fw pi-cog",
            },
            {
              label: "Billing",
              icon: "pi pi-fw pi-file",
            },
          ],
        },
      ],
    };
  },
  methods: {
    toggleMenu(event) {
      this.$refs.menu.toggle(event);
    },
    onContextRightClick(event) {
      this.$refs.contextMenu.show(event);
    },
  },
};
</script>

<style scoped lang="scss">
::v-deep(.stepsdemo-content) {
  padding: 1em 0;

  p {
    font-weight: 400;
    display: inline-block;
    vertical-align: middle;
    font-size: 18px;
    margin: 0;
  }

  i {
    vertical-align: middle;
    font-size: 1.5em;
    margin: 0;
  }
}

.contextmenu-image {
  width: 100%;
}
</style>
