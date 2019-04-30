---
title: Pagina Servizi, Creazione progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed2e8ad333121a489c450a35daf81a368cd4aba8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444731"
---
# <a name="services-page-project-designer"></a>Pagina Servizi, Progettazione progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I servizi delle applicazioni client consentono l'accesso semplificato ai servizi di accesso, ruolo e profilo di [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] da applicazioni di Windows Forms e Windows Presentation Foundation (WPF). È possibile usare la pagina **Servizi** di **Creazione progetti** per abilitare e configurare i servizi delle applicazioni client per il progetto.  
  
 Con i servizi delle applicazioni client è possibile usare un server centralizzato per autenticare gli utenti, determinare il ruolo o i ruoli assegnati a ogni utente e archiviare le impostazioni dell'applicazione per utente che possono essere condivise all'interno della rete. Per altre informazioni, vedere [Servizi applicazioni client](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Per accedere alla pagina **Servizi**, selezionare un nodo di progetto in **Esplora soluzioni** e quindi fare clic su **Proprietà** nel menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Servizi**.  
  
> [!NOTE]
> I servizi delle applicazioni client richiedono la versione completa di.NET Framework e non sono supportati in .NET Framework Client Profile. Se la casella di controllo **Attiva servizi applicazioni client** è disattivata, verificare che il **Framework di destinazione** sia impostato su.NET Framework 3.5 o versione successiva. Per visualizzare l'impostazione **Framework di destinazione** in C#, aprire Creazione progetti e quindi fare clic sulla pagina **Applicazione**. Per visualizzare l'impostazione **Framework di destinazione** in Visual Basic, aprire Creazione progetti, fare clic sulla pagina **Compilazione** e quindi fare clic su **Opzioni di compilazione avanzate**.  
  
## <a name="task-list"></a>Elenco attività  
 [Procedura: Configurare i servizi delle applicazioni client](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Configurazione**  
 Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Compilazione (pagina), Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Piattaforma**  
 Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Compilazione (pagina), Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Attiva servizi applicazione client**  
 Selezionare questa opzione per attivare i servizi dell'applicazione client. Per usare i servizi dell'applicazione client è necessario specificare i percorsi dei servizi nella pagina **Servizi**.  
  
 **Usa autenticazione di Windows**  
 Indica che il provider di autenticazione userà l'autenticazione basata su Windows, ovvero l'identità fornita dal sistema operativo Windows.  
  
 **Usa autenticazione basata su form**  
 Indica che il provider di autenticazione userà l'autenticazione basata su form. L'applicazione quindi deve fornire un'interfaccia utente per l'accesso. Per altre informazioni, vedere [Procedura: Implementare l'accesso utente con i servizi dell'applicazione client](http://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).  
  
 **Percorso servizio di autenticazione**  
 Solo con l'autenticazione basata su form. Specifica il percorso del servizio di autenticazione.  
  
 **Facoltativo: provider di credenziali**  
 Solo con l'autenticazione basata su form. Indica l'implementazione <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> che il servizio di autenticazione userà per visualizzare una finestra di dialogo di accesso quando l'applicazione chiama il metodo `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> e passa stringhe vuote o `null` per i parametri. Se si lascia questa casella vuota, è necessario passare un nome utente valido e una password al metodo <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. È necessario specificare il provider di credenziali come nome di tipo completo dell'assembly. Per altre informazioni, vedere <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> e [Nomi degli assembly](http://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). Nella sua forma più semplice, un nome di tipo qualificato dall'assembly è simile all'esempio seguente: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Percorso servizi ruoli**  
 Specifica il percorso del servizio ruoli.  
  
 **Percorso servizi impostazioni Web**  
 Specifica il percorso del servizio profili (impostazioni Web).  
  
 **Avanzate**  
 Apre la [finestra di dialogo Impostazioni avanzate per i servizi](../../ide/reference/advanced-settings-for-services-dialog-box.md), che è possibile usare per eseguire l'override del comportamento predefinito. Ad esempio, è possibile usare questa finestra di dialogo per specificare un database per l'archiviazione offline anziché usare il file system locale. Per altre informazioni, vedere [Finestra di dialogo Impostazioni avanzate per i servizi](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi applicazioni client](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Finestra di dialogo Impostazioni avanzate per i servizi](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Procedura: Configurare i servizi dell'applicazione Client](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Compilazione (pagina), Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Build Page, Project Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md)  (Pagina Compilazione, Progettazione progetti (C#))  
 [Introduzione a Creazione progetti](http://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)
