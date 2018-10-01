---
title: '&lt;Firma&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b1f829971a1e5a5d62c95c1f81fb75375f7cc74e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530729"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Firma&gt; elemento (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ &lt;firma&gt; elemento (distribuzione ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/signature-element-clickonce-deployment).  
  
Contiene le informazioni necessarie per apporre una firma digitale al manifesto della distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Note  
 Firma un manifesto di distribuzione utilizzando una firma protetta è facoltativa ma consigliato. Per altre informazioni sulla firma XML i file di vedere il World Wide Web Consortium raccomandazione "XML-Signature Syntax and Processing," descritta in [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Se si desidera firmare il manifesto, è necessario specificare l'hash per tutti i file. Impossibile firmare un manifesto con i file che non è stato eseguito l'hashing, perché gli utenti non è possibile verificare il contenuto del file senza hash.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un `Signature` elemento in un manifesto di distribuzione usato in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione.  
  
```  
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
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)



