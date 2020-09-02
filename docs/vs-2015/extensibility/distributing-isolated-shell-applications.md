---
title: Distribuzione di applicazioni shell isolate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204671"
---
# <a name="distributing-isolated-shell-applications"></a>Distribuzione di applicazioni di shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per creare un'applicazione shell isolata, è necessario installare Visual Studio e Visual Studio SDK. Per distribuire l'applicazione ai computer di altri utenti o clienti, è necessario includere un pacchetto ridistribuibile speciale per la shell isolata.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Prerequisiti per la distribuzione di applicazioni shell isolate  
  
|Nome|Descrizione|  
|----------|-----------------|  
|Visual Studio SDK|SDK necessario per sviluppare e testare le estensioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . È anche possibile usare l'SDK per creare un'istanza personalizzata della shell isolata di Visual Studio.<br /><br /> Visual Studio è un prerequisito per l'SDK.|  
|Microsoft Visual Studio ridistribuibile della shell isolata|Ridistribuibile incluso nel programma di installazione quando si compila un ambiente di strumenti in Visual Studio Isolated Shell. Il pacchetto ridistribuibile della shell isolata include il .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Creazione di un programma di installazione per l'applicazione  
 È necessario creare un programma di installazione speciale per l'applicazione shell integrata o isolata. Per altre informazioni, vedere [installazione di un'applicazione shell isolata](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Consentire aggiornamenti all'applicazione  
 Il programma di installazione deve consentire la possibilità che l'applicazione venga aggiornata, da Microsoft Update o dagli aggiornamenti della società. Per altre informazioni sugli aggiornamenti, vedere [linee guida di manutenzione per le applicazioni shell isolate](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
