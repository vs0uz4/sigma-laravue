<template>
  <div class="p-grid">
    <div class="p-col-12">
      <div class="card">
        <h4>Timeline</h4>

        <h5>Custom Timeline</h5>
        <Timeline
          :value="customEvents"
          align="alternate"
          class="customized-timeline"
        >
          <template #marker="slotProps">
            <span
              class="custom-marker p-shadow-2"
              :style="{ backgroundColor: slotProps.item.color }"
            >
              <i :class="slotProps.item.icon"></i>
            </span>
          </template>
          <template #content="slotProps">
            <Card>
              <template #title>
                {{ slotProps.item.status }}
              </template>
              <template #subtitle>
                {{ slotProps.item.date }}
              </template>
              <template #content>
                <img
                  v-if="slotProps.item.image"
                  :src="'assets/layout/images/product/' + slotProps.item.image"
                  :alt="slotProps.item.name"
                  width="200"
                  class="p-shadow-2"
                />
                <p>
                  Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                  Inventore sed consequuntur error repudiandae numquam deserunt
                  quisquam repellat libero asperiores earum nam nobis, culpa
                  ratione quam perferendis esse, cupiditate neque quas!
                </p>
                <Button label="Read more" class="p-button-text"></Button>
              </template>
            </Card>
          </template>
        </Timeline>

        <h5 style="margin-top: 5em">Horizontal - Alternate Align</h5>
        <Timeline
          :value="horizontalEvents"
          layout="horizontal"
          align="alternate"
        >
          <template #content="slotProps">
            {{ slotProps.item }}
          </template>
          <template #opposite> &nbsp; </template>
        </Timeline>
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
      customEvents: [
        {
          status: "Ordered",
          date: "15/10/2020 10:30",
          icon: "pi pi-shopping-cart",
          color: "#9C27B0",
          image: "game-controller.jpg",
        },
        {
          status: "Processing",
          date: "15/10/2020 14:00",
          icon: "pi pi-cog",
          color: "#673AB7",
        },
        {
          status: "Shipped",
          date: "15/10/2020 16:15",
          icon: "pi pi-envelope",
          color: "#FF9800",
        },
        {
          status: "Delivered",
          date: "16/10/2020 10:00",
          icon: "pi pi-check",
          color: "#607D8B",
        },
      ],
      horizontalEvents: ["2020", "2021", "2022", "2023"],
    };
  },
};
</script>

<style lang="scss" scoped>
.custom-marker {
  display: flex;
  width: 2rem;
  height: 2rem;
  align-items: center;
  justify-content: center;
  color: #ffffff;
  border-radius: 50%;
  z-index: 1;
}

::v-deep(.p-button) {
  min-width: 8em;
}

::v-deep(.p-timeline-event-content) {
  line-height: 1;
}
::v-deep(.p-timeline-event-opposite) {
  line-height: 1;
}
@media screen and (max-width: 960px) {
  ::v-deep(.customized-timeline) {
    .p-timeline-event:nth-child(even) {
      flex-direction: row !important;

      .p-timeline-event-content {
        text-align: left !important;
      }
    }
    .p-timeline-event-opposite {
      flex: 0;
    }
    .p-card {
      margin-top: 1rem;
    }
  }
}
</style>
