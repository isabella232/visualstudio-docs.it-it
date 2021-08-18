---
title: Quando creare Project tipi | Microsoft Docs
description: Informazioni su come determinare se è necessario un nuovo tipo di progetto per personalizzare Visual Studio per gli utenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c4974d4838955baecd0d0ebcaddecf13329adc14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110319"
---
# <a name="when-to-create-project-types"></a>Quando creare tipi di progetto
La creazione di un nuovo tipo di progetto costituisce una base per la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personalizzazione degli utenti. Tuttavia, la creazione di un nuovo tipo di progetto non è necessaria per tutte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le personalizzazioni. Le linee guida seguenti consentono di determinare se è necessario un nuovo tipo di progetto per lo scenario.

## <a name="create-a-new-project-type"></a>Creare un nuovo tipo Project dati
 È necessario creare un tipo di progetto se si vuole personalizzare in modo che agiti in uno o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] più dei modi seguenti:

- Partecipare alla compilazione, alla distribuzione, alle configurazioni e al controllo del codice sorgente.

- Offrire supporto per il debug.

- Visualizzare gli elementi di progetto in **Esplora soluzioni**.

- Usare la **finestra di dialogo Project** apri o **Project** nuova finestra di dialogo.

- Supporto dell'annidamento del progetto.

## <a name="extend-an-existing-project-type"></a>Estendere un tipo di Project esistente
 È possibile creare un nuovo tipo di progetto che può essere utilizzato nei modi seguenti per modificare o estendere il comportamento di un tipo di progetto esistente, ad esempio modificando il processo di compilazione per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti:

- Usare più file come singola unità.

- Visualizzare un singolo file come gerarchia di elementi secondari.

- Visualizzare un contesto di comando per gli editor.

- Visualizzare un contesto del servizio per gli editor.

## <a name="use-an-existing-project-type"></a>Usare un tipo di Project esistente
 La creazione di un nuovo progetto talvolta non è necessaria. La tabella seguente illustra le attività per cui non è necessario creare un tipo di progetto.

|Attività|Descrizione|
|----------|-----------------|
|Gestione dei comandi|Qualsiasi PACCHETTO VSPackage può gestire i comandi.|
|Compilazione di un editor|È possibile registrare editor personalizzati. Per altre informazioni, vedere [Document Windows and Editors](/previous-versions/bb165691(v=vs.100)).|
|Finestre proprietarie|È possibile creare finestre degli strumenti e documenti senza aggiungere un nuovo tipo di progetto.|
|Esposizione di proprietà nel Finestra Proprietà|Tutti gli oggetti possono esporre proprietà.|

## <a name="create-a-project-subtype"></a>Creare un sottotipo Project
 È possibile usare sottotipi di progetto per estendere un tipo di progetto gestito senza dover creare un nuovo tipo di progetto. Project sottotipi usano l'aggregazione COM per estendere i progetti gestiti scritti in Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Con l'aggregazione COM, è possibile riutilizzare gran parte dell'implementazione del sistema del progetto gestito e comunque personalizzare per un determinato scenario tramite l'aggregazione e l'uso di interfacce di supporto. Per altre informazioni sui sottotipi di progetto, [Project sottotipi](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vedi anche
- [Editor Windows documenti](/previous-versions/bb165691(v=vs.100))
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)