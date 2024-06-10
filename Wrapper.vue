<script>
  watch: {
    $route: {
      '$route.params.group_url': {
        immediate: true,
        async handler() {
          if (this.$route.params.group_url != undefined) {
            if (this.isLoggedIn) {
              await ApiHelper.getDetails(this.$route.params.group_url).then(async (response) => {
                this.groupDetails = response.data.group_details;
                await useEntitlementActions(this.$store).fetchLoggedInUserEntitlement(
                  this.groupDetails.isbn
                );
                useTitleAction(this.$store).setTitleDetails(this.groupDetails);
              });
              await useNotificationAlertsActions(this.$store).getNotificationAlerts(this.$route.params.group_url);
            }
            await this.redirectionHelper();
          }
        },
      },
    },
  },
  methods: {
    redirectionHelper() {
      if (!this.$route.meta.guest) {
          if (this.isLoggedIn && !this.$store.hasEntitlement) {
            window.location.href = '/buy-book-url';
          } else {
            window.location.href = '/login';
          }
      }
    }
  }
</script>
