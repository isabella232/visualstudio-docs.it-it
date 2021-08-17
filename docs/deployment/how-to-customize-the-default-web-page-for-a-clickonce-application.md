---
title: Personalizzare la pagina Web predefinita per l ClickOnce app
description: Informazioni sulla pagina Web generata quando si pubblica un'applicazione ClickOnce sul Web, che contiene il nome dell'applicazione e altre informazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 5185d3b49d8d1accaae7055f8bd073f9a25007dc92adff8c0978de957a55c284
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403958"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Procedura: Personalizzare la pagina Web predefinita per un'applicazione ClickOnce
Quando si pubblica ClickOnce'applicazione sul Web, viene generata e pubblicata automaticamente una pagina Web insieme all'applicazione. La pagina predefinita contiene il nome dell'applicazione e i collegamenti per installare l'applicazione, installare i prerequisiti o accedere alla Guida in MSDN.

> [!NOTE]
> I collegamenti effettivi visualizzati nella pagina dipendono dal computer in cui viene visualizzata la pagina e dai prerequisiti inclusi.

 Il nome predefinito per la pagina Web è *Publish.htm*; È possibile modificare il nome in Progettazione **Project .** Per altre informazioni, vedere [Procedura: Specificare una pagina di pubblicazione per un ClickOnce app.](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)

 La *Publish.htm* Web viene pubblicata solo se viene rilevata una versione più recente.

> [!NOTE]
> Le modifiche apportate  alle impostazioni di pubblicazione non influiranno sulla pagina *Publish.htm, con un'eccezione:* se si aggiungono o rimuovono i prerequisiti dopo la pubblicazione iniziale, l'elenco dei prerequisiti non sarà più accurato. Sarà necessario modificare il testo per il collegamento prerequisito per riflettere le modifiche.

### <a name="to-customize-the-publish-web-page"></a>Per personalizzare la pagina Web di pubblicazione

1. Pubblicare l ClickOnce appalto in un percorso Web. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce tramite la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Nel server Web aprire il file *Publish.htm* in Progettazione Web visuale o in un altro editor HTML.

3. Personalizzare la pagina nel modo desiderato e salvarla.

4. facoltativo. Per impedire Visual Studio sovrascrivere la pagina Web di pubblicazione personalizzata, deselezionare Genera automaticamente pagina **Web** di distribuzione dopo ogni pubblicazione nella finestra di dialogo **Opzioni** di pubblicazione .

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Pubblicazione ClickOnce applicazioni](../deployment/publishing-clickonce-applications.md)
- [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)