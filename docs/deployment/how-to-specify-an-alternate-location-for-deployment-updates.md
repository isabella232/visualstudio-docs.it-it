---
title: 'Procedura: specificare un percorso alternativo per la distribuzione aggiornamenti | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76be049c670fb91911be70132b459cad5e5183bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902464"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Procedura: specificare un percorso alternativo per la distribuzione degli aggiornamenti
È possibile installare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione inizialmente da un CD o una condivisione file, ma l'applicazione deve controllare gli aggiornamenti periodici sul Web. È possibile specificare un percorso alternativo per gli aggiornamenti nel manifesto della distribuzione in modo che sia possibile l'aggiornamento automatico dell'applicazione dal Web dopo l'installazione iniziale.  
  
> [!NOTE]
>  L'applicazione deve essere configurata per l'installazione in locale per usare questa funzionalità. Per altre informazioni, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Inoltre, se si installa un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione dalla rete, l'impostazione di un percorso alternativo causa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per utilizzare tale percorso per l'installazione iniziale e tutti gli aggiornamenti successivi. Se si installa l'applicazione in locale (ad esempio, da un CD), viene eseguita l'installazione iniziale usando il supporto originale e tutti gli aggiornamenti successivi verranno usato il percorso alternativo.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Specificare un percorso alternativo per gli aggiornamenti usando MageUI.exe (utilità basata su Windows Form)  
  
1.  Aprire un prompt dei comandi di .NET Framework e digitare:  
  
     **MageUI.exe**  
  
2.  Nel **File** menu, scegliere **aprire** per aprire il manifesto di distribuzione dell'applicazione.  
  
3.  Selezionare il **opzioni di distribuzione** scheda.  
  
4.  Nella casella di testo denominato **posizione avviare**, immettere l'URL della directory che conterrà il manifesto di distribuzione degli aggiornamenti dell'applicazione.  
  
5.  Salvare il manifesto di distribuzione.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Specificare un percorso alternativo per gli aggiornamenti usando Mage.exe  
  
1. Aprire un prompt dei comandi di .NET Framework.  
  
2. Impostare il percorso di aggiornamento usando il comando seguente. In questo esempio *HelloWorld.exe.application* è il percorso per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione, che ha sempre l'estensione Application, e *<http://adatum.com/Update/Path>* è l'URL che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] controllerà gli aggiornamenti dell'applicazione.  
  
    **Mage-aggiornare HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3. Salvare il file.  
  
   > [!NOTE]
   >  È ora necessario firmare nuovamente il file con *Mage.exe*. Per altre informazioni, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Se si installa l'applicazione da un supporto offline, ad esempio un CD, e il computer è online, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] controlla prima di tutto l'URL specificato per il `<deploymentProvider>` tag nel manifesto di distribuzione per determinare se il percorso di aggiornamento contiene una versione più recente del applicazione. In caso affermativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installa l'applicazione direttamente da qui, anziché dalla directory di installazione iniziale, e common language runtime (CLR) determina l'attendibilità dell'applicazione usando il livello `<deploymentProvider>`. Se il computer è offline, o `<deploymentProvider>` non è raggiungibile, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installazioni da CD e CLR concede l'attendibilità in base al punto di installazione; per un'installazione da CD, ciò significa che l'applicazione riceve l'attendibilità totale. Tutti gli aggiornamenti successivi erediterà tale livello di attendibilità.  
  
 Tutti i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni che usano `<deploymentProvider>` deve dichiarare in modo esplicito le autorizzazioni necessarie nel relativo manifesto dell'applicazione, in modo che l'applicazione non riceve diversi livelli di attendibilità in computer diversi.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)