---
title: 'Procedura: specificare un percorso alternativo per gli aggiornamenti della distribuzione | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c71586c43fa1a71205d61ae21fb94c267daf497d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381912"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Procedura: Specificare un percorso alternativo per gli aggiornamenti della distribuzione
È possibile installare l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione inizialmente da un CD o una condivisione file, ma l'applicazione deve verificare la presenza di aggiornamenti periodici sul Web. È possibile specificare un percorso alternativo per gli aggiornamenti nel manifesto di distribuzione in modo che l'applicazione possa aggiornarsi dal Web dopo l'installazione iniziale.

> [!NOTE]
> Per usare questa funzionalità, l'applicazione deve essere configurata per l'installazione locale. Per ulteriori informazioni, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Inoltre, se si installa un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione dalla rete, l'impostazione di un percorso alternativo comporta [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'utilizzo di tale percorso sia per l'installazione iniziale che per tutti gli aggiornamenti successivi. Se si installa l'applicazione in locale (ad esempio, da un CD), l'installazione iniziale viene eseguita utilizzando il supporto originale e tutti gli aggiornamenti successivi utilizzeranno il percorso alternativo.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Specificare un percorso alternativo per gli aggiornamenti usando MageUI.exe (utilità basata su Windows Forms)

1. Aprire un prompt dei comandi di .NET Framework e digitare:

     **mageui.exe**

2. Scegliere **Apri** dal menu **file** per aprire il manifesto di distribuzione dell'applicazione.

3. Selezionare la scheda **Opzioni di distribuzione**.

4. Nella casella di testo denominata **percorso di avvio**immettere l'URL della directory che conterrà il manifesto di distribuzione per gli aggiornamenti dell'applicazione.

5. Salvare il manifesto della distribuzione.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Specificare un percorso alternativo per gli aggiornamenti usando Mage.exe

1. Aprire un prompt dei comandi di .NET Framework.

2. Impostare il percorso di aggiornamento usando il comando seguente. In questo esempio *HelloWorld.exe. Application* è il percorso del [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione, che ha sempre l'estensione. Application e `http://adatum.com/Update/Path` è l'URL che verificherà la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] disponibilità di aggiornamenti dell'applicazione.

    **Mage-Update HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/update/path**

3. Salvare il file.

   > [!NOTE]
   > È ora necessario firmare nuovamente il file con *Mage.exe*. Per ulteriori informazioni, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 Se l'applicazione viene installata da un supporto offline, ad esempio un CD, e il computer è online, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] controlla prima di tutto l'URL specificato dal `<deploymentProvider>` tag nel manifesto di distribuzione per determinare se il percorso di aggiornamento contiene una versione più recente dell'applicazione. In caso contrario, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installa l'applicazione direttamente da questa posizione, anziché dalla directory di installazione iniziale, e il Common Language Runtime (CLR) determina il livello di attendibilità dell'applicazione tramite `<deploymentProvider>` . Se il computer è offline o `<deploymentProvider>` non è raggiungibile, viene [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installato dal CD e CLR concede l'attendibilità in base al punto di installazione. per un'installazione CD, significa che l'applicazione riceve l'attendibilità totale. Tutti gli aggiornamenti successivi erediteranno il livello di attendibilità.

 Tutte le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni che utilizzano `<deploymentProvider>` devono dichiarare in modo esplicito le autorizzazioni necessarie nel manifesto dell'applicazione, in modo che l'applicazione non riceva diversi livelli di attendibilità in computer diversi.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)