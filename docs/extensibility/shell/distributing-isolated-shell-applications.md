---
title: Distribuzione di applicazioni Shell isolata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6e9b7ded8d24e4d252d29338d89bd176648511a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="distributing-isolated-shell-applications"></a>Distribuzione di applicazioni Shell isolata
Per creare un'applicazione shell isolata, è necessario installare Visual Studio e Visual Studio SDK. Per distribuire l'applicazione per le macchine di altri utenti o clienti, è necessario includere un pacchetto ridistribuibile speciale per la shell isolata.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Prerequisiti per la distribuzione di applicazioni Isolated Shell  
  
|nome|Descrizione|  
|----------|-----------------|  
|Visual Studio SDK|il SDK è necessario per sviluppare e testare le estensioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È anche possibile utilizzare il SDK per creare un'istanza personalizzata della shell di Visual Studio isolated.<br /><br /> Visual Studio è un prerequisito per il SDK.|  
|Shell Redistributable isolata di Microsoft Visual Studio|Il pacchetto ridistribuibile di includere nel programma di installazione quando si compila un ambiente di strumenti di Visual Studio shell isolata. Il pacchetto ridistribuibile di Shell isolato include .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Creazione di un programma di installazione per l'applicazione  
 È necessario creare un programma di installazione speciali per l'applicazione shell isolata o integrata. Per ulteriori informazioni, vedere [l'installazione di un'applicazione Shell isolata](installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Consentire gli aggiornamenti per l'applicazione  
 Il programma di installazione deve consentire la possibilità che l'applicazione verrà aggiornata per gli aggiornamenti Microsoft o per gli aggiornamenti della società. Per ulteriori informazioni sugli aggiornamenti, vedere [linee guida per la manutenzione di applicazione Shell isolata](servicing-guidelines-for-isolated-shell-applications.md).