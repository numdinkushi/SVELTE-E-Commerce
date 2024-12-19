<script lang="ts">
  import * as Card from "$lib/components/ui/card";
  import { formatCurrency, formatNumber } from "$lib/utils";

  type DashboardCardProps = {
    title: string;
    subtitle: string;
    body: string;
  };

  let { data } = $props();
  let { productData, userData, salesData } = $derived(data);
</script>

<div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-3">
  <div class="">
    {@render dashboardCard({
      title: "Total Sales",
      subtitle: `${formatNumber(salesData.numberOfSales)} orders`,
      body: formatCurrency(salesData?.amount),
    })}
  </div>
  <div class="">
    {@render dashboardCard({
      title: "Total Sales",
      subtitle: "This Month",
      body: "$324324",
    })}
  </div>
  <div class="">
    {@render dashboardCard({
      title: "Total Sales",
      subtitle: "This Month",
      body: "$324324",
    })}
  </div>
</div>

{#snippet dashboardCard({ title, subtitle, body }: DashboardCardProps)}
  <Card.Root>
    <Card.Header>
      <Card.Title>{title}</Card.Title>
      <Card.Description>{subtitle}</Card.Description>
    </Card.Header>
    <Card.Content>
      <p>{body}</p>
    </Card.Content>
  </Card.Root>
{/snippet}
