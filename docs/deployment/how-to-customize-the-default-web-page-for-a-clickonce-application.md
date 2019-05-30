---
title: Personalizzare una pagina web predefinita per l'applicazione ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 66d304be4e2435b6ec1ecafe8aeb473b83fa1033
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263325"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Procedura: Personalizzare la pagina Web predefinita per un'applicazione ClickOnce
Quando si pubblica un'applicazione ClickOnce per il Web, una pagina Web viene automaticamente generata e pubblicata insieme all'applicazione. La pagina predefinita contiene il nome dell'applicazione e i collegamenti per installare l'applicazione, installare i prerequisiti o accedere alla Guida in MSDN.

> [!NOTE]
> I collegamenti effettivi che viene visualizzato nella pagina dipendono dal computer in cui viene visualizzata la pagina e ciò che sono inclusi i prerequisiti.

 Il nome predefinito per la pagina Web viene *Publish. htm*; è possibile modificare il nome nel **creazione progetti**. Per altre informazioni, vedere [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Il *Publish. htm* pagina Web viene pubblicata solo se viene rilevata una versione più recente.

> [!NOTE]
> Le modifiche apportate al **pubblica** non influisce sulle impostazioni di *Publish. htm* pagina, con un'unica eccezione: se si aggiunge o rimuove i prerequisiti dopo la pubblicazione inizialmente, l'elenco dei prerequisiti verrà non è più possibile accurate. È necessario modificare il testo per il collegamento dei prerequisiti in modo da riflettere le modifiche.

### <a name="to-customize-the-publish-web-page"></a>Per personalizzare la pagina Web pubblica

1. Pubblicare l'applicazione ClickOnce in un percorso Web. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Nel server Web, aprire il *Publish. htm* file in Visual Web Designer o un altro editor di codice HTML.

3. Personalizzare la pagina in base alle esigenze e salvarlo.

4. Facoltativo. Per impedire la sovrascrittura della pagina Web pubblica personalizzate di Visual Studio, deselezionare **genera automaticamente pagina Web di distribuzione dopo ogni pubblicazione** nel **Publish Options** nella finestra di dialogo.

## <a name="see-also"></a>Vedere anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)