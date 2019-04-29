---
title: '&lt;Firma&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
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
ms.openlocfilehash: 1c636a4178cf278c2bb0ad75f4e78b94758dda30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927489"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Firma&gt; elemento (distribuzione ClickOnce)
Contiene le informazioni necessarie per apporre una firma digitale al manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml

      <Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Note
 Firma un manifesto di distribuzione utilizzando una firma protetta è facoltativa ma consigliato. Per altre informazioni sulla firma di file XML, vedere il World Wide Web Consortium raccomandazione "XML-Signature Syntax and Processing," descritta in [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).

 Se si desidera firmare il manifesto, è necessario specificare l'hash per tutti i file. Impossibile firmare un manifesto con i file che non è stato eseguito l'hashing, perché gli utenti non è possibile verificare il contenuto del file senza hash.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra un `Signature` elemento in un manifesto di distribuzione usato in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione.

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