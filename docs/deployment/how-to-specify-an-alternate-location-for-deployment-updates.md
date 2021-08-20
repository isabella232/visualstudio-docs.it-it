---
title: Specificare un percorso alternativo per gli aggiornamenti della distribuzione
description: Informazioni su come specificare un percorso alternativo per gli aggiornamenti per l'ClickOnce nel manifesto della distribuzione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 9c9db27ae54519c56a2c8f7c60454a823c59dfff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160647"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Procedura: Specificare un percorso alternativo per gli aggiornamenti della distribuzione
È possibile installare l'applicazione inizialmente da un CD o da una condivisione file, ma l'applicazione deve verificare la disponibilità [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di aggiornamenti periodici sul Web. È possibile specificare un percorso alternativo per gli aggiornamenti nel manifesto della distribuzione in modo che l'applicazione possa aggiornarsi dal Web dopo l'installazione iniziale.

> [!NOTE]
> L'applicazione deve essere configurata per l'installazione locale per usare questa funzionalità. Per altre informazioni, vedere [Procedura dettagliata: Distribuire manualmente un'ClickOnce applicazione](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Inoltre, se si installa un'applicazione dalla rete, l'impostazione di un percorso alternativo comporta l'uso di tale percorso sia per l'installazione iniziale che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per tutti gli aggiornamenti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] successivi. Se si installa l'applicazione in locale, ad esempio da un CD, l'installazione iniziale viene eseguita usando il supporto originale e tutti gli aggiornamenti successivi useranno il percorso alternativo.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Specificare un percorso alternativo per gli aggiornamenti usando MageUI.exe (Windows'utilità basata su Form)

1. Aprire un prompt .NET Framework prompt dei comandi e digitare:

     **mageui.exe**

2. Scegliere **Apri** dal menu File **per** aprire il manifesto della distribuzione dell'applicazione.

3. Selezionare la scheda **Opzioni di distribuzione**.

4. Nella casella di testo denominata **Posizione di** avvio immettere l'URL della directory che conterrà il manifesto della distribuzione per gli aggiornamenti dell'applicazione.

5. Salvare il manifesto della distribuzione.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Specificare un percorso alternativo per gli aggiornamenti usando Mage.exe

1. Aprire un prompt dei comandi di .NET Framework.

2. Impostare il percorso di aggiornamento usando il comando seguente. In questo *esempio,HelloWorld.exe.application* è il percorso del manifesto dell'applicazione, che ha sempre l'estensione .application, e è l'URL che verifica la disponibilità di aggiornamenti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `http://adatum.com/Update/Path` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.

    **Mage -Update HelloWorld.exe.application -ProviderUrl http: \/ /adatum.com/Update/Path**

3. Salvare il file.

   > [!NOTE]
   > È ora necessario firmare nuovamente il file con *Mage.exe*. Per altre informazioni, vedere [Procedura dettagliata: Distribuire manualmente un'ClickOnce applicazione](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 Se si installa l'applicazione da un supporto offline, ad esempio un CD, e il computer è online, controlla innanzitutto l'URL specificato dal tag nel manifesto della distribuzione per determinare se il percorso di aggiornamento contiene una versione più recente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `<deploymentProvider>` dell'applicazione. In caso contrario, installa l'applicazione direttamente da questa posizione, anziché dalla directory di installazione iniziale, e Common Language Runtime (CLR) determina il livello di attendibilità [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione usando `<deploymentProvider>` . Se il computer è offline o non è raggiungibile, viene installato dal CD e CLR concede l'attendibilità in base al punto di installazione. Per un'installazione da CD, ciò significa che l'applicazione riceve l'attendibilità `<deploymentProvider>` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totale. Tutti gli aggiornamenti successivi erediteranno tale livello di attendibilità.

 Tutte le applicazioni che usano devono dichiarare in modo esplicito le autorizzazioni necessarie nel manifesto dell'applicazione, in modo che l'applicazione non riceva livelli di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `<deploymentProvider>` attendibilità diversi in computer diversi.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce di distribuzione](../deployment/clickonce-deployment-manifest.md)
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)