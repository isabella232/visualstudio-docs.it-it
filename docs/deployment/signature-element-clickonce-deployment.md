---
title: Elemento&gt; della firma &lt;(distribuzione ClickOnce) | Microsoft Docs
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
ms.openlocfilehash: f69dcec6bbee5358184b74a71274cb26e4de60b3
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806838"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>elemento&gt; della firma &lt;(distribuzione ClickOnce)
Contiene le informazioni necessarie per apporre una firma digitale al manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml

      <Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Note
 La firma di un manifesto di distribuzione con una firma della busta è facoltativa, ma consigliata. Per ulteriori informazioni sulla firma di file XML, vedere la World Wide Web Consortium raccomandazione, "sintassi e elaborazione della firma XML", descritta in [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/).

 Se si desidera firmare il manifesto, è necessario fornire gli hash per tutti i file. Un manifesto con file non con hash non può essere firmato perché gli utenti non possono verificare il contenuto dei file senza hash.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un elemento `Signature` in un manifesto di distribuzione usato in una distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

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
- [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)