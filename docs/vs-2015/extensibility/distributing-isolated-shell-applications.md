---
title: La distribuzione di applicazioni della Shell isolata | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7388a5b723b5346f1f653024215c16ba474fa48a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532243"
---
# <a name="distributing-isolated-shell-applications"></a>La distribuzione di applicazioni della Shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [distribuzione di applicazioni isolate Shell](https://docs.microsoft.com/visualstudio/extensibility/distributing-isolated-shell-applications).  
  
Per creare un'applicazione shell isolata, è necessario installare Visual Studio e Visual Studio SDK. Per distribuire l'applicazione per le macchine di altri utenti o clienti, è necessario includere un pacchetto ridistribuibile speciale per la shell isolata.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Prerequisiti per la distribuzione delle applicazioni della Shell isolata  
  
|nome|Descrizione|  
|----------|-----------------|  
|Visual Studio SDK|il SDK è necessario per sviluppare e testare le estensioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. È anche possibile usare il SDK per creare l'istanza della shell isolata di Visual Studio.<br /><br /> Visual Studio è un prerequisito per il SDK.|  
|Microsoft Visual Studio Isolated Shell Redistributable|Il pacchetto ridistribuibile di includere nel programma di installazione quando si compila un ambiente con strumenti in Visual Studio isolated shell. Il pacchetto ridistribuibile di Shell isolato include .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Creazione di un programma di installazione per l'applicazione  
 È necessario creare un programma di installazione speciali per l'applicazione di shell integrata o isolata. Per altre informazioni, vedere [installazione di un'applicazione Shell isolata](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Consentire gli aggiornamenti all'applicazione  
 Il programma di installazione deve consentire la possibilità che l'applicazione verrà aggiornata da Microsoft Update o da aggiornamenti dell'azienda. Per altre informazioni sugli aggiornamenti, vedere [linee guida per la manutenzione per le applicazioni della Shell isolata](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

