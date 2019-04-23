---
title: Impostazioni per le configurazioni di Debug c# del progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd484422cdae8cfc04cab169feefdd452f178a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056679"
---
# <a name="project-settings-for--c-debug-configurations"></a>Impostazioni di progetto per le configurazioni di debug C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare le impostazioni di progetto per una configurazione di debug c# nella **pagine delle proprietà** finestra, come descritto in [configurazioni Debug e Release](../debugger/how-to-set-debug-and-release-configurations.md). Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.  
  
> [!WARNING]
>  Questo argomento non si applica alle app di Windows Store. Vedere [avviare una sessione di debug (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
## <a name="BKMK_Debug_tab"></a> Scheda Debug  
  
|**Impostazione**|**Descrizione**|  
|-----------------|---------------------|  
|**Configurazione**|Imposta la modalità per la compilazione dell'applicazione. Le opzioni disponibili sono **Attiva (Debug)**, **Debug**, **Release**, **Tutte le configurazioni**.|  
|**Azione di avvio**|Questo gruppo di controlli specifica l'azione che verrà eseguita quando si sceglie Avvia dal menu Debug.<br /><br /> -   **Avvia progetto** è l'azione predefinita e avvia il progetto di avvio per il debug. Per altre informazioni, vedere [scegliendo il progetto di avvio](http://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Avvia programma esterno** consente di avviare un programma che non fa parte di un progetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e di stabilire una connessione al programma. Per altre informazioni, vedere [connessione a un programma in esecuzione](http://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Avvia browser con URL** consente di eseguire il debug di un'applicazione Web.|  
|**Argomenti della riga di comando**|Specifica gli argomenti della riga di comando per il programma da sottoporre a debug. Il nome del comando è il nome del programma specificato in Avvia programma esterno. Se l'opzione Azione di avvio è impostata su Avvia URL, non è possibile specificare gli argomenti della riga di comando.|  
|**Directory di lavoro**|Specifica la cartella di lavoro del programma sottoposto a debug. In [!INCLUDE[csprcs](../includes/csprcs-md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione, che per impostazione predefinita è \bin\debug.|  
|**Usa computer remoto**|Il nome di un computer remoto in cui verrà eseguita l'applicazione a scopo di debug o un' [nome di server Msvsmon](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Il percorso del file EXE sul computer remoto è specificato dalla proprietà Percorso output nella cartella Proprietà di configurazione, categoria Compila. Il percorso deve essere una directory condivisibile del computer remoto.|  
|**Abilita debug codice non gestito**|Consente di eseguire il debug delle chiamate al codice Win32 nativo (non gestito) dall'applicazione gestita in uso.|  
|**Abilita debug SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
  
## <a name="BKMK_Build_tab"></a> Scheda compilazione  
  
|Impostazione|Descrizione|  
|-------------|-----------------|  
|**Simboli di compilazione condizionale:**|Le costanti DEBUG e TRACE vengono definite in questa posizione.<br /><br /> Esse attivano la compilazione condizionale della [Classe Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) e della [Classe Trace](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Quando sono definite, i metodi delle classi Debug e Trace generano l'output per la [finestra di output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.<br /><br /> -Debug è in genere definito nella versione di Debug di un programma e non definito nella versione di rilascio.<br />-Trace è generalmente definito nelle versioni Debug e rilascio.|  
|**Ottimizza codice**|Questa impostazione deve rimanere disattivata nella versione di debug, a meno che non venga rilevato un bug solo nel codice ottimizzato. L'esecuzione del debug di un codice ottimizzato è più complessa poiché le istruzioni non corrispondono direttamente alle istruzioni presenti nelle finestre del codice sorgente.|  
|**Percorso di output:**|Generalmente impostato su bin\Debug per l'esecuzione del debug.|  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)
