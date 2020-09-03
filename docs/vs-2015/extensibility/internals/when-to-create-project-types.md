---
title: Quando creare i tipi di progetto | Microsoft Docs
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
ms.openlocfilehash: 5b5bc2bacb53973bd552b983b742e4f9e68fe31b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687703"
---
# <a name="when-to-create-project-types"></a>Quando creare tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La creazione di un nuovo tipo di progetto costituisce una base per la personalizzazione degli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utenti. Tuttavia, la creazione di un nuovo tipo di progetto non è necessaria per tutte le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] personalizzazioni. Le linee guida seguenti consentono di determinare se è necessario un nuovo tipo di progetto per lo scenario in uso.  
  
## <a name="create-a-new-project-type"></a>Creare un nuovo tipo di progetto  
 È necessario creare un tipo di progetto se si desidera personalizzare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per agire in uno o più dei modi seguenti:  
  
- Partecipare a compilazione, distribuzione, configurazioni e controllo del codice sorgente.  
  
- Offrire supporto per il debug.  
  
- Visualizza gli elementi del progetto in **Esplora soluzioni**.  
  
- Utilizzare la finestra di dialogo **Apri progetto** o **nuovo progetto** .  
  
- Supporto dell'annidamento del progetto.  
  
## <a name="extend-an-existing-project-type"></a>Estendi un tipo di progetto esistente  
 Potrebbe essere necessario creare un nuovo tipo di progetto che può utilizzare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nei modi seguenti per modificare o estendere il comportamento di un tipo di progetto esistente, ad esempio per modificare il processo di compilazione per i [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] progetti:  
  
- Usare più file come singola unità.  
  
- Visualizza un singolo file come una gerarchia di elementi secondari.  
  
- Visualizzare un contesto di comando intorno agli editor.  
  
- Visualizza un contesto del servizio per gli editor.  
  
## <a name="use-an-existing-project-type"></a>Usa un tipo di progetto esistente  
 A volte non è necessario creare un nuovo progetto. Nella tabella seguente vengono illustrate le attività per cui non è necessario creare un tipo di progetto.  
  
|Attività|Descrizione|  
|----------|-----------------|  
|Gestione dei comandi|Qualsiasi pacchetto VSPackage può gestire i comandi.|  
|Compilazione di un editor|È possibile registrare gli editor personalizzati. Per altre informazioni, vedere [Document Windows and Editors](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Finestre proprietarie|È possibile creare finestre degli strumenti e del documento senza aggiungere un nuovo tipo di progetto.|  
|Esposizione delle proprietà nell'Finestra Proprietà|Tutti gli oggetti possono esporre proprietà.|  
  
## <a name="create-a-project-subtype"></a>Creare un sottotipo di progetto  
 È possibile utilizzare sottotipi di progetto per estendere un tipo di progetto gestito senza dover creare un nuovo tipo di progetto. I sottotipi di progetto utilizzano l'aggregazione COM per estendere i progetti gestiti scritti in Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Con l'aggregazione COM, è possibile riutilizzare gran parte dell'implementazione del sistema di progetti gestiti e comunque personalizzare per uno scenario specifico tramite l'aggregazione e l'utilizzo di interfacce di supporto. Per ulteriori informazioni sui sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di documento e editor](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Elenco di controllo: creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
