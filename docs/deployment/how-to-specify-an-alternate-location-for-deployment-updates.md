---
title: 'Procedura: specificare un percorso alternativo per gli aggiornamenti della distribuzione Documenti Microsoft'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0484e36bb857f5d08382f86f42b2e09dda21616
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037337"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Procedura: Specificare un percorso alternativo per gli aggiornamenti della distribuzione
È possibile [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installare l'applicazione inizialmente da un CD o da una condivisione file, ma l'applicazione deve verificare la disponibilità di aggiornamenti periodici sul Web. È possibile specificare un percorso alternativo per gli aggiornamenti nel manifesto di distribuzione in modo che l'applicazione possa aggiornarsi dal Web dopo l'installazione iniziale.

> [!NOTE]
> L'applicazione deve essere configurata per l'installazione locale per l'utilizzo di questa funzionalità. Per ulteriori informazioni, vedere [Procedura dettagliata: distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Inoltre, se si [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installa un'applicazione dalla rete, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'impostazione di un percorso alternativo determina l'utilizzo di tale percorso sia per l'installazione iniziale che per tutti gli aggiornamenti successivi. Se si installa l'applicazione in locale, ad esempio da un CD, l'installazione iniziale viene eseguita utilizzando il supporto originale e tutti gli aggiornamenti successivi utilizzeranno il percorso alternativo.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Specificare un percorso alternativo per gli aggiornamenti utilizzando MageUI.exe (utilità basata su Windows Form)

1. Aprire un prompt dei comandi di .NET Framework e digitare:

     **mageui.exe**

2. Scegliere **Apri** dal **Open** menu File per aprire il manifesto di distribuzione dell'applicazione.

3. Selezionare la scheda **Opzioni di distribuzione**.

4. Nella casella di testo **Percorso di avvio**immettere l'URL della directory che conterrà il manifesto di distribuzione per gli aggiornamenti dell'applicazione.

5. Salvare il manifesto di distribuzione.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Specificare un percorso alternativo per gli aggiornamenti utilizzando Mage.exe

1. Aprire un prompt dei comandi di .NET Framework.

2. Impostare il percorso di aggiornamento utilizzando il comando seguente. In questo esempio, *HelloWorld.exe.application* è [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] il percorso del manifesto dell'applicazione, che ha sempre l'estensione application ed `http://adatum.com/Update/Path` è l'URL che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] controllerà la disponibilità di aggiornamenti dell'applicazione.

    **Mage -Aggiornare HelloWorld.exe.application -ProviderUrl http:\//adatum.com/Update/Path**

3. Salvare il file.

   > [!NOTE]
   > A questo punto è necessario firmare nuovamente il file con *Mage.exe*. Per ulteriori informazioni, vedere [Procedura dettagliata: distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 Se si installa l'applicazione da un supporto offline, ad [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esempio un CD, `<deploymentProvider>` e il computer è online, controlla innanzitutto l'URL specificato dal tag nel manifesto di distribuzione per determinare se il percorso di aggiornamento contiene una versione più recente dell'applicazione. In caso [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affermativo, l'applicazione viene installata direttamente da lì, anziché dalla directory di installazione iniziale, e Common Language Runtime (CLR) determina il livello di attendibilità dell'applicazione utilizzando `<deploymentProvider>`. Se il computer non `<deploymentProvider>` è in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] linea o non è raggiungibile, esegue le installazioni dal CD e CLR concede l'attendibilità in base al punto di installazione. per l'installazione di un CD, significa che l'applicazione riceve l'attendibilità totale. Tutti gli aggiornamenti successivi erediteranno tale livello di attendibilità.

 Tutte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le `<deploymentProvider>` applicazioni che utilizzano devono dichiarare in modo esplicito le autorizzazioni necessarie nel manifesto dell'applicazione, in modo che l'applicazione non riceva livelli diversi di attendibilità in computer diversi.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)