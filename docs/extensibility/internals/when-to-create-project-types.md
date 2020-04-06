---
title: Quando si creano i tipi di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703426"
---
# <a name="when-to-create-project-types"></a>Quando creare tipi di progetto
La creazione di un nuovo tipo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetto fornisce una base per la personalizzazione per gli utenti. Tuttavia, la creazione di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nuovo tipo di progetto non è necessaria per tutte le personalizzazioni. Le linee guida seguenti consentono di determinare se è necessario un nuovo tipo di progetto per lo scenario.

## <a name="create-a-new-project-type"></a>Creare un nuovo tipo di progetto
 È necessario creare un tipo di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto se si desidera personalizzare in modo che agisca in uno o più dei modi seguenti:

- Partecipare alla compilazione, alla distribuzione, alle configurazioni e al controllo del codice sorgente.

- Offrire il supporto per il debug.

- Visualizzare gli elementi del progetto in **Esplora soluzioni**.

- Utilizzare la finestra di dialogo **Apri progetto** o **Nuovo progetto.**

- Supportare la nidificazione dei progetti.

## <a name="extend-an-existing-project-type"></a>Estendere un tipo di progetto esistenteExtend an Existing Project Type
 È possibile creare un nuovo tipo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetto che può essere utilizzato nei modi seguenti per modificare o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] estendere il comportamento di un tipo di progetto esistente, ad esempio la modifica del processo di compilazione per i progetti:You might want to create a new project type that can use in the following ways to modify or extend the behavior of an existing project type, for example, modifying the build process for projects:

- Lavorare con più file come una singola unità.

- Visualizzare un singolo file come una gerarchia di elementi secondari.

- Visualizzare un contesto di comando intorno agli editor.

- Visualizzare un contesto di servizio per gli editor.

## <a name="use-an-existing-project-type"></a>Utilizzo di un tipo di progetto esistente
 La creazione di un nuovo progetto a volte non è necessaria. Nella tabella seguente vengono illustrate le attività per le quali non è necessario creare un tipo di progetto.

|Attività|Descrizione|
|----------|-----------------|
|Gestione dei comandi|Qualsiasi VSPackage può gestire i comandi.|
|Creazione di un editor|Gli editor personalizzati possono essere registrati. Per ulteriori informazioni, consultate [Finestre ed editor di documenti.](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)|
|Finestre proprietarie|È possibile creare finestre degli strumenti e del documento senza aggiungere un nuovo tipo di progetto.|
|Esposizione di proprietà nella finestra Proprietà|Tutti gli oggetti possono esporre proprietà.|

## <a name="create-a-project-subtype"></a>Creazione di un sottotipo di progetto
 È possibile utilizzare i sottotipi di progetto per estendere un tipo di progetto gestito senza dover creare un nuovo tipo di progetto. I sottotipi di progetto utilizzano l'aggregazione COM per estendere i progetti gestiti scritti in Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Con l'aggregazione COM, è possibile riutilizzare gran parte dell'implementazione del sistema del progetto gestito e personalizzare comunque per un particolare scenario tramite l'aggregazione e l'utilizzo di interfacce di supporto. Per ulteriori informazioni sui sottotipi di progetto, vedere [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vedere anche
- [Finestre ed editor di documenti](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
