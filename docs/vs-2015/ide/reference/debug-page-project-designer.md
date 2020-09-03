---
title: Pagina Debug, Creazione progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 006662d7c07ba0498fff4617eca3fdc7c631d37b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660793"
---
# <a name="debug-page-project-designer"></a>Pagina Debug, Progettazione progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> Questo argomento non si applica alle app di Windows Store. Vedere [Avviare una sessione di debug (VB, C#, C++ e XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) in Windows Dev Center.

 Usare la pagina **Debug** di **Creazione progetti** per impostare le proprietà per il comportamento di debug in un progetto Visual Basic o C#.

 Per accedere alla pagina **Debug** selezionare un nodo del progetto in **Esplora soluzioni**. Scegliere**proprietà** _NomeProgetto_dal menu **progetto** . Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Debug**.

## <a name="configuration-and-platform"></a>Configurazione e Piattaforma
 Le opzioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.

 **Configurazione** Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni possibili sono **Debug** (impostazione predefinita), **Rilascio** o **Tutte le configurazioni**. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).

 **Piattaforma** Specifica le impostazioni della piattaforma da visualizzare o modificare. Le scelte possono includere **Qualsiasi CPU** (impostazione predefinita), **x64** e **x86**. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).

## <a name="start-action"></a>Azione di avvio
 **Azione di avvio** indica l'elemento da avviare quando viene eseguito il debug dell'applicazione: il progetto, un programma personalizzato, un URL o nulla. Per impostazione predefinita, questa opzione è impostata su **Avvia progetto**. L'impostazione **Avvia azione** nella pagina **Debug** determina il valore della proprietà `StartAction`.

 **Avvia progetto** Scegliere questa opzione per specificare che il file eseguibile (per i progetti applicazione Windows e applicazione console) deve essere avviato quando viene eseguito il debug dell'applicazione. Questa opzione è selezionata per impostazione predefinita.

 **Avvia programma esterno** Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato un programma specifico.

 **Avvia browser con URL** Scegliere questa opzione per specificare che è necessario accedere a un particolare URL durante il debug dell'applicazione.

## <a name="start-options"></a>Opzioni di avvio
 **Argomenti della riga di comando** In questa casella di testo immettere gli argomenti della riga di comando da utilizzare per il debug.

 **Directory di lavoro** In questa casella di testo immettere la directory da cui verrà avviato il progetto. oppure fare clic sul pulsante Sfoglia (**...**) per scegliere una directory.

 **Usa computer remoto** Per eseguire il debug dell'applicazione da un computer remoto, selezionare questa casella di controllo e immettere il percorso del computer remoto nella casella di testo.

## <a name="enable-debuggers"></a>Abilita debugger
 **Abilita debug codice non gestito** Questa opzione specifica se è supportato il debug del codice nativo. Selezionare questa casella di controllo se si effettuano chiamate a oggetti COM o se si avvia un programma personalizzato scritto in codice nativo che chiama il progetto ed è necessario eseguire il debug del codice nativo. Deselezionare questa casella di controllo per disabilitare il debug di codice non gestito. Questa casella di controllo è deselezionata per impostazione predefinita.

 **Abilita debug SQL Server** Selezionare o deselezionare questa casella di controllo per abilitare o disabilitare il debug di procedure SQL dall'applicazione Visual Basic. Questa casella di controllo è deselezionata per impostazione predefinita.

 **Abilita il processo di hosting di Visual Studio** Selezionare questa casella di controllo per abilitare il processo di hosting di Visual Studio. Questa casella di controllo è selezionata per impostazione predefinita. Per altre informazioni, vedere [Processo di hosting (vshost.exe)](../../ide/hosting-process-vshost-exe.md).

 Per il debug in un'area di sicurezza è necessario abilitare questa opzione e selezionare la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** nella [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md).

## <a name="see-also"></a>Vedere anche
 Debug nelle impostazioni di progetto di [Visual Studio](../../debugger/debugging-in-visual-studio.md) [per le configurazioni di debug C#](../../debugger/project-settings-for-csharp-debug-configurations.md) [impostazioni di progetto per una configurazione di debug Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md) [gestione delle proprietà di debug](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68) [procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [procedura: creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)
