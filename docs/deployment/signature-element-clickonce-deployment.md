---
title: '&lt;Elemento &gt; Signature (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento Signature contiene le informazioni necessarie per firmare digitalmente questo manifesto di distribuzione. La firma di un manifesto di distribuzione è facoltativa ma consigliata.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 8312a9660ca621857b835f43f9e43a173c93240e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035605"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Elemento &gt; Signature (ClickOnce distribuzione)
Contiene le informazioni necessarie per apporre una firma digitale al manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Osservazioni
 La firma di un manifesto di distribuzione tramite una firma envelope è facoltativa, ma consigliata. Per altre informazioni sulla firma di file XML, vedere la raccomandazione World Wide Web Consortium, "Sintassi ed elaborazione della firma XML", descritta in [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Se si vuole firmare il manifesto, è necessario specificare gli hash per tutti i file. Non è possibile firmare un manifesto con file senza hash, perché gli utenti non possono verificare il contenuto dei file senza hash.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra un `Signature` elemento in un manifesto di distribuzione usato in una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione.

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

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto della distribuzione](../deployment/clickonce-deployment-manifest.md)
