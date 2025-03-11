// Script mở khóa Premium cho 4English
const url = $request.url;
const isSubscriptionEndpoint = url.includes("/v1/user/subscription");

if (isSubscriptionEndpoint) {
  const response = {
    status: "active",
    is_premium: true,
    expires_at: "2099-01-01T00:00:00Z",
    features: {
      unlimited_access: true,
      offline_mode: true,
      advanced_dictionary: true,
    },
  };
  $done({ body: JSON.stringify(response) });
} else {
  $done({});
}