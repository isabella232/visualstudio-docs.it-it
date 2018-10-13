---
title: La distribuzione di applicazioni della Shell isolata | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: d05e6a88c9da52492a49462880a04e578feadb5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305812"
---
# <a name="distributing-isolated-shell-applications"></a>La distribuzione di applicazioni della Shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

