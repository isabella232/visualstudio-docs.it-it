---
title: Impostazioni delle pagine delle proprietà per i progetti Web | Microsoft Docs
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
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cb7cd3f8c3678d37feb2267f68ab5d2b3d970e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150860"
---
# <a name="property-pages-settings-for-web-projects"></a>Impostazioni delle pagine delle proprietà per i progetti Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare le impostazioni delle proprietà per la configurazione di debug di un sito Web nella finestra di dialogo **Pagine delle proprietà**, come descritto in [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md). Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Cartella Proprietà di configurazione (categoria Opzioni di avvio)  
  
|**Impostazione**|**Descrizione**|  
|-----------------|---------------------|  
|**Azione di avvio**|Intestazione sotto la quale sono raggruppate le opzioni correlate all'avvio dell'applicazione.|  
|**Usa pagina corrente**|Specifica la pagina corrente come punto di avvio per il debug.|  
|**Pagina specifica:**|Specifica la pagina Web da cui iniziare la procedura di debug.|  
|**Avvia programma esterno:**|Specifica il comando per l'avvio del programma da sottoporre a debug.|  
|**Argomenti della riga di comando:**|Specifica gli argomenti relativi al comando riportato sopra.|  
|**Directory di lavoro:**|Specifica la cartella di lavoro del programma sottoposto a debug. In [!INCLUDE[csprcs](../includes/csprcs-md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione, che per impostazione predefinita è \bin\debug.|  
|**URL di avvio**|Specifica la posizione dell'applicazione Web da sottoporre a debug.|  
|**Non aprire una pagina. Attendi una richiesta da un'applicazione esterna**|Specifica di attendere una richiesta da un'applicazione esterna. Questa opzione non avvia Internet Explorer né altre applicazioni. Esegue semplicemente le operazioni di preparazione necessarie per eseguire il debug su richiesta di un'applicazione.|  
|**Server**|Intestazione sotto la quale sono raggruppate le opzioni correlate al server da utilizzare.|  
|**Usa server Web predefinito**|Specifica di utilizzare il server Web predefinito.|  
|**Usa server personalizzato**|Consente di immettere l'URL di base da utilizzare come server.|  
|**Debugger**|Intestazione sotto la quale sono raggruppate le opzioni correlate al tipo di debug da eseguire.|  
|**Debug di ASP.NET**|Attiva il debug di pagine ASP scritte per la piattaforma di sviluppo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. È necessario specificare un URL in **Avvia URL**.|  
|**Debug codice nativo**|Consente di eseguire il debug delle chiamate al codice Win32 nativo (non gestito) dall'applicazione gestita in uso.|  
|**Debug SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
|**Debug di Silverlight**|Consente di eseguire il debug dei componenti di Silverlight.|  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)
