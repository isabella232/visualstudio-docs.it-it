---
title: '&lt;&gt;elemento Description (distribuzione ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadf4a0b525e5603247748edd63516dc26d8a0b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187755"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;&gt;elemento Description (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica le informazioni sull'applicazione utilizzate per creare una presenza Shell e un elemento **Installazione applicazioni** nel pannello di controllo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `description` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1` . Non contiene elementi figlio e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`publisher`|Obbligatorio. Identifica il nome della società usato per il posizionamento delle icone nel menu **Start** di Windows e l'elemento installazione **applicazioni** nel pannello di controllo, quando la distribuzione è configurata per l'installazione.|  
|`product`|Obbligatorio. Identifica il nome completo del prodotto. Utilizzato come titolo per l'icona installata nel menu **Start** di Windows.|  
|`suiteName`|facoltativo. Identifica una sottocartella all'interno della `publisher` cartella nel menu **Start** di Windows.|  
|`supportUrl`|facoltativo. Specifica un URL di supporto visualizzato nell'elemento **Installazione applicazioni** nel pannello di controllo. Viene inoltre creato un collegamento a questo URL per il supporto dell'applicazione nel menu **Start** di Windows, quando la distribuzione è configurata per l'installazione.|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento Description è obbligatorio in tutte le configurazioni di distribuzione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un `description` elemento in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto di distribuzione. Questo esempio di codice fa parte di un esempio più ampio fornito per l'argomento [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
