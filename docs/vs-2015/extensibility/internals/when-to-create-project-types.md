---
title: Quando creare tipi di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 682fc88fb616fbe2617fe6d336a35bf6fbc30e9f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954816"
---
# <a name="when-to-create-project-types"></a>Quando creare tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Creare un nuovo tipo di progetto fornisce una base per la personalizzazione [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per gli utenti. Tuttavia, creare un nuovo tipo di progetto non è obbligatorio per tutti i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] personalizzazioni. Le seguenti linee guida dovrebbero consentire di determinare se un nuovo tipo di progetto è obbligatorio per il proprio scenario.  
  
## <a name="create-a-new-project-type"></a>Creare un nuovo tipo di progetto  
 È necessario creare un tipo di progetto se si desidera personalizzare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] di agire in uno o più dei modi seguenti:  
  
-   Partecipa a compilazione, distribuzione, le configurazioni e controllo del codice sorgente.  
  
-   Offrono supporto per il debug.  
  
-   Visualizzare gli elementi di progetto in **Esplora soluzioni**.  
  
-   Usare la **Apri progetto** oppure **nuovo progetto** nella finestra di dialogo.  
  
-   Supporta l'annidamento di progetto.  
  
## <a name="extend-an-existing-project-type"></a>Estendere un tipo di progetto esistente  
 Si potrebbe voler creare un nuovo tipo di progetto utilizzabili [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nei modi seguenti per modificare o estendere il comportamento di un tipo di progetto esistente, ad esempio, la modifica del processo di compilazione per [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] progetti:  
  
-   Funziona con più file come singola unità.  
  
-   Visualizzare un singolo file come una gerarchia di elementi secondari.  
  
-   Visualizzare un contesto del comando per gli editor.  
  
-   Visualizzare un contesto del servizio per gli editor.  
  
## <a name="use-an-existing-project-type"></a>Usare un tipo di progetto esistente  
 Crea un nuovo progetto in alcuni casi non è necessario. La tabella seguente illustra le attività che non è necessario creare un tipo di progetto per.  
  
|Attività|Descrizione|  
|----------|-----------------|  
|Gestione dei comandi|Qualsiasi pacchetto VSPackage può gestire i comandi.|  
|Creazione di un editor|Editor personalizzati possono essere registrati. Per altre informazioni, vedere [editor e documenti Windows](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Proprietario windows|È possibile creare documenti e degli strumenti windows senza l'aggiunta di un nuovo tipo di progetto.|  
|Esposizione di proprietà nella finestra proprietà|Tutti gli oggetti possono esporre le proprietà.|  
  
## <a name="create-a-project-subtype"></a>Creare un sottotipo di progetto  
 È possibile usare i sottotipi di progetto per estendere un tipo di progetto gestito senza la necessità di creare un nuovo tipo di progetto. Sottotipi di progetto usano aggregazione COM per estendere i progetti gestiti, scritti in Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Con l'aggregazione COM, è possibile riutilizzare gran parte dell'implementazione del sistema del progetto gestito e comunque personalizzare per un determinato scenario tramite l'aggregazione e l'uso del supporto di interfacce. Per altre informazioni sulle sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Editor e documenti Windows](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
