---
hide:
  - navigation
---

# KapitWifi

This page discusses the details and implementation of KapitWifi as shown in the official tutorial video.

<iframe width="560" height="315" src="https://www.youtube.com/embed/i2g7GO60N5U?si=lVAdrsKtWj4Z0apN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## What is KapitWifi?

KapitWifi is a coinless Wi-Fi vending system that uses Unified Prepaid Wi-Fi System technology to improve and modernize existing prepaid Wi-Fi solutions such as PisoWifi, which uses coin machines to buy prepaid wifi.

## Benefits

### Clients

- Cheap and dynamic access to internet (cheap compared to mobile data)
- Free access to Wikipedia for students (optional)

### Operators

- Passive income
- Technical know-how is not required (Plug and Forget Setup)
- Fast ROI (Cheap investment), PHP 3500.00 to [buy the whole setup](https://kapitwifi.ph/store).

[^1]: [Official KapitWifi FAQs](https://kapitwifi.ph/#faqs)

[^2]: [Official KapitWifi Tutorial](https://www.youtube.com/watch?v=i2g7GO60N5U)

## The KapitWifi Network (Unified Prepaid Wi-Fi System)

The KapitWifi network is a collection of individual access points that have the same name (SSID: `KapitWifi Coinless Vendo`) with access to the internet.

These access points have operators and these operators gain income when clients (customers) uses WiFi via their operated access point.

!!! Info "Speculation"

    Password-less configuration is important for dynamic client access (client can switch WiFi networks any time, any where, within the range of a KapitWifi access point). However, client authentication is still needed to top-up and utilize prepaid wifi. Clients can authenticate themselves by logging in to https://login.kapitwifi.ph, this is usually done through automatic redirection so users are always redirected to the mentioned link when they try to access the internet without authentication.

## Who pays, who profits, and how

The clients are the customers who want to avail prepaid wifi. The operators own the WiFi access points and contribute to the servicable range of KapitWifi, thereby increasing the range and size of the KapitWifi Unified System network.

KapitWifi uses digital banks such as [GCash](https://gcash.com/) or [Maya](https://www.maya.ph/) to simplify online transactions. KapitWifi also uses traditional payment systems such Visa or Mastercard. Clients can pay with cash when operators have e-vouchers/vouchers to sell. KapitWifi incurs a 15% system charge to every prepaid wifi sale, regardless of the amount of money paid. KapitWifi incur a monthly subscription fee of PHP 35.00 to the operators when they use features such as 'printed vouchers'.

Operators receive the remaining 85% as revenue, which is divided among the operators based on the amount of time the client is connected to internet through an operator's access point. If there are no other access points that the client has used, then the whole 85% is paid to the only operator who operates the access point the client was connected to.

Operator revenue is distributed every 12:01 AM to their own KapitWifi wallet, which can be withdrawn to their own GCash or Maya wallet.

## How to buy Prepaid Wifi

Clients buy prepaid wifi by connecting to the KapitWifi network and logging in to their KapitWifi account. They pay by using but not limited to, digital banks such as [GCash](https://gcash.com/) or [Maya](https://www.maya.ph/), or traditional systems like Visa or Mastercard.

During the process, internet connection is free of charge, when they login or make payments.
However, clients are blocked to access everything except payment systems or the KapitWifi login/signup page. KapitWifi does this by remotely configuring these access points to restrict access. Read more about this in this [relevant documention](../implementation/network.md#omada-devices).

### Vouchers

Vouchers are payment options that the clients can avail with cash on hand. To generate these vouchers, the operator must buy these vouchers using their own money so that they can distribute these to the clients.
