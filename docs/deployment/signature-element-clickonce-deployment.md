---
title: '&lt;&gt;Elemento Signature (distribuzione ClickOnce) | Microsoft Docs'
description: L'elemento Signature contiene le informazioni necessarie per la firma digitale del manifesto della distribuzione. La firma di un manifesto di distribuzione è facoltativa ma consigliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7a86236087bdbff8cf82ca4821573f9f799d019
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349282"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;&gt;Elemento Signature (distribuzione ClickOnce)
Contiene le informazioni necessarie per apporre una firma digitale al manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Osservazioni
 La firma di un manifesto di distribuzione con una firma della busta è facoltativa, ma consigliata. Per ulteriori informazioni sulla firma di file XML, vedere la World Wide Web Consortium raccomandazione "sintassi e elaborazione della firma XML" descritta in [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Se si desidera firmare il manifesto, è necessario fornire gli hash per tutti i file. Un manifesto con file non con hash non può essere firmato perché gli utenti non possono verificare il contenuto dei file senza hash.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato un `Signature` elemento in un manifesto di distribuzione utilizzato in una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione.

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>Vedere anche
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
