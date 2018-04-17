---
title: '&lt;Descrizione&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4701bc77350d080ef9ad9c1eb56b80c344b0ff0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Descrizione&gt; elemento (distribuzione di ClickOnce)
Identifica le informazioni sull'applicazione utilizzate per creare una shell e un **Aggiungi / Rimuovi programmi** nel Pannello di controllo.  
  
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
 L'elemento `description` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1`. Non contiene elementi figlio e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`publisher`|Obbligatorio. Identifica il nome della società utilizzato per il posizionamento delle icone nelle finestre **avviare** menu e **Aggiungi / Rimuovi programmi** nel Pannello di controllo, quando la distribuzione è configurata per l'installazione.|  
|`product`|Obbligatorio. Identifica il nome del prodotto completo. Utilizzato come il titolo dell'icona di cui è installato in Windows **avviare** menu.|  
|`suiteName`|Facoltativo. Identifica una sottocartella all'interno di `publisher` cartella nelle finestre **avviare** menu.|  
|`supportUrl`|Facoltativo. Specifica un URL di supporto disponibile nella finestra di **Aggiungi / Rimuovi programmi** nel Pannello di controllo. Viene inoltre creato un collegamento a questo URL per il supporto di applicazioni in Windows **avviare** menu quando la distribuzione è configurata per l'installazione.|  
  
## <a name="remarks"></a>Note  
 L'elemento description è obbligatorio in tutte le configurazioni di distribuzione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato un `description` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione. Questo esempio di codice fa parte di un esempio più esaustivo disponibile per il [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) argomento.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)