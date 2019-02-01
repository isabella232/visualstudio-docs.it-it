---
title: '&lt;Descrizione&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c926da377688b1248daa01f015cda7914434a36
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013899"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Descrizione&gt; elemento (distribuzione ClickOnce)
Identifica le informazioni sull'applicazione usate per creare una shell e un **Aggiungi / Rimuovi programmi** nel Pannello di controllo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `description` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1` . Non contiene alcun elemento figlio e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`publisher`|Obbligatorio. Identifica il nome della società usato per il posizionamento delle icone in di Windows **avviare** dal menu e i **Aggiungi / Rimuovi programmi** nel Pannello di controllo, durante la distribuzione è configurata per l'installazione.|  
|`product`|Obbligatorio. Identifica il nome del prodotto completo. Utilizzato come titolo dell'icona installata in di Windows **avviare** menu.|  
|`suiteName`|Facoltativo. Identifica una sottocartella all'interno di `publisher` cartella di Windows **avviare** menu.|  
|`supportUrl`|Facoltativo. Specifica un URL di supporto disponibile nella finestra di **Aggiungi / Rimuovi programmi** nel Pannello di controllo. Viene inoltre creato un collegamento a questo URL per il supporto dell'applicazione in di Windows **avviare** menu, durante la distribuzione è configurata per l'installazione.|  
  
## <a name="remarks"></a>Note  
 L'elemento description è obbligatorio in tutte le configurazioni di distribuzione.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un `description` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto della distribuzione. Questo esempio di codice è parte di un esempio più esaustivo disponibile per il [del manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) argomento.  
  
```xml  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)