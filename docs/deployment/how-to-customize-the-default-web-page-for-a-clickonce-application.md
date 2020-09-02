---
title: Personalizzare la pagina Web predefinita per l'applicazione ClickOnce
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ee4c1211840f17afe371961dea644372cd63efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382471"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Procedura: Personalizzare la pagina Web predefinita per un'applicazione ClickOnce
Quando si pubblica un'applicazione ClickOnce sul Web, una pagina Web viene generata e pubblicata automaticamente insieme all'applicazione. La pagina predefinita contiene il nome dell'applicazione e i collegamenti per installare l'applicazione, installare i prerequisiti o accedere alla guida su MSDN.

> [!NOTE]
> I collegamenti effettivi visualizzati nella pagina dipendono dal computer in cui viene visualizzata la pagina e dai prerequisiti inclusi.

 Il nome predefinito per la pagina Web è *Publish.htm*; è possibile modificare il nome in **Progettazione progetti**. Per altre informazioni, vedere [procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 La pagina Web *Publish.htm* viene pubblicata solo se viene rilevata una versione più recente.

> [!NOTE]
> Le modifiche apportate alle impostazioni di **pubblicazione** non influiscono sulla pagina *Publish.htm* , con un'unica eccezione: se si aggiungono o rimuovono prerequisiti dopo la pubblicazione iniziale, l'elenco dei prerequisiti non sarà più accurato. Per riflettere le modifiche, sarà necessario modificare il testo per il collegamento dei prerequisiti.

### <a name="to-customize-the-publish-web-page"></a>Per personalizzare la pagina Web pubblica

1. Pubblicare l'applicazione ClickOnce in un percorso Web. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Nel server Web aprire il file di *Publish.htm* in Visual Web designer o in un altro editor HTML.

3. Personalizzare la pagina nel modo desiderato e salvarla.

4. facoltativo. Per impedire a Visual Studio di sovrascrivere la pagina Web di pubblicazione personalizzata, deselezionare **genera automaticamente pagina Web di distribuzione dopo ogni pubblicazione** nella finestra di dialogo **Opzioni di pubblicazione** .

## <a name="see-also"></a>Vedere anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)