<template>
  <div class="p-grid overlay-demo">
    <div class="p-col-12 p-lg-6">
      <div class="card p-fluid">
        <h5>Dialog</h5>
        <Dialog
          header="Dialog"
          v-model:visible="display"
          :breakpoints="{ '960px': '75vw' }"
          :style="{ width: '30vw' }"
          :modal="true"
        >
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat. Duis aute irure dolor in
            reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
            pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
            culpa qui officia deserunt mollit anim id est laborum.
          </p>
          <template #footer>
            <Button
              label="Dismiss"
              @click="close"
              icon="pi pi-check"
              class="p-button-secondary"
            />
          </template>
        </Dialog>
        <div class="p-grid">
          <div class="p-col-12">
            <Button label="Show" icon="pi pi-external-link" @click="open" />
          </div>
        </div>
      </div>
      <div class="card p-fluid">
        <h5>Overlay Panel</h5>
        <div class="p-grid p-formgrid">
          <div class="p-col-6">
            <Button
              type="button"
              label="Image"
              @click="toggle"
              class="p-button-success"
            />
            <OverlayPanel ref="op" appendTo="body" :showCloseIcon="true">
              <img
                src="assets/layout/images/nature/nature9.jpg"
                alt="Nature 9"
              />
            </OverlayPanel>
          </div>
          <div class="p-col-6">
            <Button
              type="button"
              label="DataTable"
              @click="toggleDataTable"
              class="p-button-success"
            />
            <OverlayPanel
              ref="op2"
              appendTo="body"
              :showCloseIcon="true"
              id="overlay_panel"
              style="width: 450px"
            >
              <DataTable
                :value="products"
                v-model:selection="selectedProduct"
                selectionMode="single"
                :paginator="true"
                :rows="5"
                @row-select="onProductSelect"
              >
                <Column field="name" header="Name" :sortable="true"></Column>
                <Column header="Image">
                  <template #body="slotProps">
                    <img
                      :src="
                        'assets/layout/images/product/' + slotProps.data.image
                      "
                      :alt="slotProps.data.image"
                      class="product-image"
                    />
                  </template>
                </Column>
                <Column field="price" header="Price" :sortable="true">
                  <template #body="slotProps">
                    {{ formatCurrency(slotProps.data.price) }}
                  </template>
                </Column>
              </DataTable>
            </OverlayPanel>
          </div>
        </div>
      </div>
    </div>
    <div class="p-col-12 p-lg-6">
      <div class="card p-fluid">
        <h5>Confirmation</h5>
        <Button
          label="Delete"
          icon="pi pi-trash"
          class="p-button-danger"
          @click="openConfirmation"
        />
        <Dialog
          header="Confirmation"
          v-model:visible="displayConfirmation"
          :style="{ width: '350px' }"
          :modal="true"
        >
          <div class="confirmation-content">
            <i
              class="pi pi-exclamation-triangle p-mr-3"
              style="font-size: 2rem"
            />
            <span>Are you sure you want to proceed?</span>
          </div>
          <template #footer>
            <Button
              label="No"
              icon="pi pi-times"
              @click="closeConfirmation"
              class="p-button-text"
            />
            <Button
              label="Yes"
              icon="pi pi-check"
              @click="closeConfirmation"
              class="p-button-text"
              autofocus
            />
          </template>
        </Dialog>
      </div>
      <div class="card">
        <h5>Sidebar</h5>
        <Sidebar v-model:visible="visibleLeft" :baseZIndex="1000">
          <h1 style="fontweight: normal">Left Sidebar</h1>
          <Button
            type="button"
            @click="visibleLeft = false"
            label="Save"
            class="p-button-success"
            style="margin-right: 0.25em"
          />
          <Button
            type="button"
            @click="visibleLeft = false"
            label="Cancel"
            class="p-button-secondary"
          />
        </Sidebar>

        <Sidebar
          v-model:visible="visibleRight"
          :baseZIndex="1000"
          position="right"
        >
          <h1 style="fontweight: normal">Right Sidebar</h1>
          <Button
            type="button"
            @click="visibleRight = false"
            label="Save"
            class="p-button-success"
            style="margin-right: 0.25em"
          />
          <Button
            type="button"
            @click="visibleRight = false"
            label="Cancel"
            class="p-button-secondary"
          />
        </Sidebar>

        <Sidebar v-model:visible="visibleTop" :baseZIndex="1000" position="top">
          <h1 style="fontweight: normal">Top Sidebar</h1>
          <Button
            type="button"
            @click="visibleTop = false"
            label="Save"
            class="p-button-success"
            style="margin-right: 0.25em"
          />
          <Button
            type="button"
            @click="visibleTop = false"
            label="Cancel"
            class="p-button-secondary"
          />
        </Sidebar>

        <Sidebar
          v-model:visible="visibleBottom"
          :baseZIndex="1000"
          position="bottom"
        >
          <h1 style="fontweight: normal">Bottom Sidebar</h1>
          <Button
            type="button"
            @click="visibleBottom = false"
            label="Save"
            class="p-button-success"
            style="margin-right: 0.25em"
          />
          <Button
            type="button"
            @click="visibleBottom = false"
            label="Cancel"
            class="p-button-secondary"
          />
        </Sidebar>

        <Sidebar
          v-model:visible="visibleFull"
          :baseZIndex="1000"
          position="full"
        >
          <h1 style="fontweight: normal">Full Screen</h1>
          <Button
            type="button"
            @click="visibleFull = false"
            label="Save"
            class="p-button-success"
            style="margin-right: 0.25em"
          />
          <Button
            type="button"
            @click="visibleFull = false"
            label="Cancel"
            class="p-button-secondary"
          />
        </Sidebar>

        <Button
          icon="pi pi-arrow-right"
          class="p-button-warning"
          @click="visibleLeft = true"
          style="margin-right: 0.25em"
        />
        <Button
          icon="pi pi-arrow-left"
          class="p-button-warning"
          @click="visibleRight = true"
          style="margin-right: 0.25em"
        />
        <Button
          icon="pi pi-arrow-down"
          class="p-button-warning"
          @click="visibleTop = true"
          style="margin-right: 0.25em"
        />
        <Button
          icon="pi pi-arrow-up"
          class="p-button-warning"
          @click="visibleBottom = true"
          style="margin-right: 0.25em"
        />
        <Button
          icon="pi pi-external-link"
          class="p-button-warning"
          @click="visibleFull = true"
        />
      </div>
    </div>
    <div class="p-col-12 p-lg-6">
      <div class="card">
        <h5>Tooltip</h5>
        <div class="p-formgroup-inline">
          <div class="p-field">
            <InputText
              type="text"
              placeholder="Username"
              v-tooltip="'Your username'"
            />
          </div>

          <Button
            type="button"
            label="Save"
            icon="pi pi-check"
            v-tooltip="'Click to proceed'"
          />
        </div>
      </div>
    </div>
    <div class="p-col-12 p-lg-6">
      <div class="card">
        <h5>ConfirmPopup</h5>
        <ConfirmPopup></ConfirmPopup>
        <Button
          ref="popup"
          @click="confirm($event)"
          icon="pi pi-check"
          label="Confirm"
          class="p-mr-2"
        ></Button>
      </div>
    </div>
  </div>
</template>

<script>
import ProductService from "../../service/ProductService";
import Layout from "../../layout/App";
export default {
  layout: Layout,
  data() {
    return {
      display: false,
      displayConfirmation: false,
      visibleLeft: false,
      visibleRight: false,
      visibleTop: false,
      visibleBottom: false,
      visibleFull: false,
      products: null,
      selectedProduct: null,
    };
  },
  productService: null,
  created() {
    this.productService = new ProductService();
  },
  mounted() {
    this.productService
      .getProductsSmall()
      .then((data) => (this.products = data));
  },
  methods: {
    open() {
      this.display = true;
    },
    close() {
      this.display = false;
    },
    openConfirmation() {
      this.displayConfirmation = true;
    },
    closeConfirmation() {
      this.displayConfirmation = false;
    },
    toggle(event) {
      this.$refs.op.toggle(event);
    },
    toggleDataTable(event) {
      this.$refs.op2.toggle(event);
    },
    formatCurrency(value) {
      return value.toLocaleString("en-US", {
        style: "currency",
        currency: "USD",
      });
    },
    onProductSelect(event) {
      this.$refs.op.hide();
      this.$toast.add({
        severity: "info",
        summary: "Product Selected",
        detail: event.data.name,
        life: 3000,
      });
    },
    confirm(event) {
      this.$confirm.require({
        target: event.currentTarget,
        message: "Are you sure you want to proceed?",
        icon: "pi pi-exclamation-triangle",
        accept: () => {
          this.$toast.add({
            severity: "info",
            summary: "Confirmed",
            detail: "You have accepted",
            life: 3000,
          });
        },
        reject: () => {
          this.$toast.add({
            severity: "error",
            summary: "Rejected",
            detail: "You have rejected",
            life: 3000,
          });
        },
      });
    },
  },
};
</script>

<style scoped>
p {
  line-height: 1.5;
  margin: 0;
}

.product-image {
  width: 50px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
}

.confirmation-content {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
