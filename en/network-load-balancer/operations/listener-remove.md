# Deleting a listener

{% list tabs %}

- Management console

   To delete a [listener](../concepts/listener.md) for your network load balancer:

   1. Open the **Load Balancer** section in the folder to delete the listener from.
   1. Select the network load balancer for deleting the listener.
   1. Under **Listeners**, click ![image](../../_assets/vertical-ellipsis.svg) in the line of the listener to delete.
   1. In the menu that opens, click **Remove listener**.

- CLI

   {% include [cli-install](../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../_includes/default-catalogue.md) %}

   To delete a listener for your network load balancer, run this command:

   ```bash
   yc load-balancer network-load-balancer remove-listener <load balancer ID or name> \
      --listener-name=<listener name>
   ```

   You can get the load balancer ID and name with a [list of network load balancers in the folder](load-balancer-list.md#list) and the listener name with [network load balancer details](load-balancer-list.md#get).

- {{ TF }}

   {% include [terraform-definition](../../_tutorials/terraform-definition.md) %}

   For more information about {{ TF }}, [see our documentation](../../tutorials/infrastructure-management/terraform-quickstart.md#install-terraform).

   To delete a listener of a network load balancer created with {{ TF }}:
   1. Open the {{ TF }} configuration file and delete the fragment with the listener description.

      ```hcl
      resource "yandex_lb_network_load_balancer" "foo" {
        ...
        listener {
          name = "<listener name>"
          port = <port number>
          external_address_spec {
            ip_version = "<IP version: ipv4 or ipv6>"
          }
        }
        ...
      }
      ```

   1. Make sure the settings are correct.

      {% include [terraform-validate](../../_includes/mdb/terraform/validate.md) %}

   1. Delete the network load balancer.

      {% include [terraform-apply](../../_includes/mdb/terraform/apply.md) %}

- API

   To remove a network load balancer's listener, use the [removeListener](../api-ref/NetworkLoadBalancer/removeListener.md) REST API method for the [NetworkLoadBalancer](../api-ref/NetworkLoadBalancer/index.md) resource or the [NetworkLoadBalancerService/RemoveListener](../api-ref/grpc/network_load_balancer_service.md#RemoveListener) gRPC API call and provide the following in the request:

   * Load balancer ID in the `networkLoadBalancerId` parameter.
   * Listener name in the `listenerName` parameter.

   You can get the load balancer ID with a [list of network load balancers in the folder](load-balancer-list.md#list) and the listener name with [network load balancer details](load-balancer-list.md#get).

{% endlist %}