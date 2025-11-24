Consent Manager Installation Instructions

1. Extract the contents of this zip file
2. Place the files in your website directory
3. Add the following code to your HTML page, inside the <head> tag:

<link rel="stylesheet" id="silktide-consent-manager-css" href="path-to-css/silktide-consent-manager.css">
<script src="path-to-js/silktide-consent-manager.js"></script>
<script>
silktideCookieBannerManager.updateCookieBannerConfig({
  background: {
    showBackground: true
  },
  cookieIcon: {
    position: "bottomLeft"
  },
  cookieTypes: [
    {
      id: "essential_cookies",
      name: "Essential cookies",
      description: "<p>These cookies are necessary for our website to function properly and cannot be disabled. They enable core functions such as page navigation, access to secure areas, form submissions, and storing your cookie preferences.</p>",
      required: true,
      onAccept: function() {
        console.log('Add logic for the required Essential cookies here');
      }
    },
    {
      id: "analytics",
      name: "Analytics",
      description: "<p>We use Google Analytics to understand how visitors interact with our website. These cookies help us analyze page views, user behavior, and traffic sources. IP anonymization is enabled to protect your privacy. Provider: Google Ireland Limited, Gordon House, Barrow Street, Dublin 4, Ireland.</p>",
      required: false,
      onAccept: function() {
        gtag('consent', 'update', {
          analytics_storage: 'granted',
        });
        dataLayer.push({
          'event': 'consent_accepted_analytics',
        });
      },
      onReject: function() {
        gtag('consent', 'update', {
          analytics_storage: 'denied',
        });
      }
    },
    {
      id: "advertising_marketing",
      name: "Advertising &amp; Marketing",
      description: "<p>These cookies are used to deliver personalized ads and to measure the effectiveness of advertising campaigns. They support platforms such as Google Ads, Facebook/Instagram (Meta Pixel), and TikTok. Providers include Google Ireland Limited, Meta Platforms Ireland Ltd., and TikTok Technology Limited.</p>",
      required: false,
      onAccept: function() {
        gtag('consent', 'update', {
          ad_storage: 'granted',
          ad_user_data: 'granted',
          ad_personalization: 'granted',
        });
        dataLayer.push({
          'event': 'consent_accepted_advertising_marketing',
        });
      },
      onReject: function() {
        gtag('consent', 'update', {
          ad_storage: 'denied',
          ad_user_data: 'denied',
          ad_personalization: 'denied',
        });
      }
    },
    {
      id: "functional",
      name: "Functional",
      description: "These cookies enable additional functionality and help ensure a consistent user experience. For example, services like Google Fonts may load fonts directly from Google servers to display text properly across devices.",
      required: false,
      onAccept: function() {
        console.log('Add accept logic for Functional');
      },
      onReject: function() {
        console.log('Add reject logic for Functional');
      }
    }
  ],
  text: {
    banner: {
      description: "<p>We use cookies on our site to enhance your user experience, provide personalized content, and analyze our traffic. <a href=\"https://your-website.com/cookie-policy\" target=\"_blank\">Cookie Policy.</a></p>",
      acceptAllButtonText: "Accept all",
      acceptAllButtonAccessibleLabel: "Accept all cookies",
      rejectNonEssentialButtonText: "Reject non-essential",
      rejectNonEssentialButtonAccessibleLabel: "Reject non-essential",
      preferencesButtonText: "Preferences",
      preferencesButtonAccessibleLabel: "Toggle preferences"
    },
    preferences: {
      title: "Customize your cookie preferences",
      description: "<p>We respect your right to privacy. You can choose not to allow some types of cookies. Your cookie preferences will apply across our website.</p>",
      creditLinkText: "",
      creditLinkAccessibleLabel: ""
    }
  }
});
</script>
