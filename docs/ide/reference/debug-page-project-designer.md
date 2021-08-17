---
title: Pagina Debug, Progettazione progetti
description: Usare la pagina Debug di Progettazione Project per impostare le proprietà di debug in un progetto Visual Basic o C#. Vedere questo articolo per le descrizioni delle impostazioni.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5a79f12eda3d166b2154e71faefcc60e2457049ada19b5b3cd0d558e6c40e012
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429511"
---
# <a name="debug-page-project-designer"></a>Pagina Debug, Progettazione progetti

Usare la pagina **Debug** di **Creazione progetti** per impostare le proprietà per il comportamento di debug in un progetto Visual Basic o C#.

Per accedere alla pagina **Debug** selezionare un nodo del progetto in **Esplora soluzioni**. Nel menu **Project** scegliere **\<ProjectName> Proprietà**. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Debug**.

> [!NOTE]
> Questo argomento non si applica alle app UWP. Per le app UWP, vedere [Avviare una sessione di debug (VB, C#, C++ e XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="configuration-and-platform"></a>Configurazione e Piattaforma

Le opzioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.

**Configuration**

Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni possibili sono **Debug** (impostazione predefinita), **Rilascio** o **Tutte le configurazioni**.

**Piattaforma**

Specifica le impostazioni della piattaforma da visualizzare o modificare. Le scelte possono includere **Qualsiasi CPU** (impostazione predefinita), **x64** e **x86**.

## <a name="start-action"></a>Azione di avvio

**Azione di avvio** indica l'elemento da avviare durante il debug dell'applicazione: il progetto, un programma personalizzato, un URL o nulla. Per impostazione predefinita, questa opzione è impostata su **Avvia progetto**. L'impostazione **Avvia azione** nella pagina **Debug** determina il valore della proprietà `StartAction`.

**Avvia progetto**

Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato il file eseguibile (per i progetti Applicazione Windows e Applicazione console). Questa opzione è selezionata per impostazione predefinita.

**Avvia programma esterno**

Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato un programma specifico.

**Avvia il browser con URL**

Scegliere questa opzione per specificare che durante il debug dell'applicazione è necessario accedere a un URL specifico.

## <a name="start-options"></a>Opzioni di avvio

**Argomenti della riga di comando**

Immettere in questa casella di testo gli argomenti della riga di comando da usare per il debug.

**Directory di lavoro**

Immettere in questa casella di testo la directory da cui verrà avviato il progetto oppure fare clic sul pulsante Sfoglia (**...**) per scegliere una directory.

**Usa computer remoto**

Per il debug dell'applicazione da un computer remoto selezionare questa casella di controllo e immettere il percorso al computer remoto nella casella di testo.

## <a name="debugger-engines"></a>Motori di debugger

**Abilita debug del codice nativo**

Questa opzione specifica se è supportato il debug del codice nativo. Selezionare questa casella di controllo se si effettuano chiamate a oggetti COM o se si avvia un programma personalizzato scritto in codice nativo che chiama il progetto ed è necessario eseguire il debug del codice nativo. Deselezionare questa casella di controllo per disabilitare il debug di codice non gestito. Questa casella di controllo è deselezionata per impostazione predefinita.

**Abilita debug SQL Server**

Selezionare o deselezionare questa casella di controllo per abilitare o disabilitare il debug delle routine SQL dall'applicazione Visual Basic. Questa casella di controllo è deselezionata per impostazione predefinita.

## <a name="see-also"></a>Vedi anche

- [Presentazione del debugger](../../debugger/debugger-feature-tour.md)
- [Project Impostazioni per le configurazioni di debug C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project Impostazioni per una configurazione Visual Basic debug](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Proteggere ClickOnce app](../../deployment/securing-clickonce-applications.md)
- [Procedura: Creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)
