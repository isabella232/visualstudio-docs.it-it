---
title: '&lt;customErrorReporting&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: cf4a723fe5986287859134d0f97868a19956f5a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252018"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; elemento (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica un URI da visualizzare quando si verifica un errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Note  
 Questo elemento è facoltativo. In caso contrario, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Visualizza una finestra di dialogo di errore che mostra lo stack dell'eccezione. Se il `customErrorReporting` è presente, l'elemento [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] invece verrà visualizzato l'URI indicato dal `uri` parametro. L'URI di destinazione includerà la classe di eccezione esterna, la classe di eccezione interna e il messaggio di eccezione interna come parametri.  
  
 Usare questo elemento per aggiungere funzionalità di segnalazione all'applicazione. Poiché l'URI generato contiene informazioni sul tipo di errore, il sito Web è possibile analizzare tali informazioni e visualizzazione, ad esempio, una schermata di risoluzione dei problemi appropriata.  
  
## <a name="example"></a>Esempio  
 Il frammento seguente illustra il `customErrorReporting` elemento, con l'URI generato che potrebbe produrre.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)



