---
title: Estendere test codificati dell'interfaccia utente e registrazioni delle azioni
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 3060014002b2e34443741dc654cf29df53278fe2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664917"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Estendere test codificati dell'interfaccia utente e registrazioni delle azioni

Il framework di test per i test codificati dell'interfaccia utente e le registrazioni delle azioni non supportano tutte le interfacce utente disponibili, e quindi potrebbero non supportare l'interfaccia utente specifica di cui eseguire il test. Ad esempio, non si può creare immediatamente un test codificato dell'interfaccia utente o una registrazione delle azioni per un foglio di calcolo di Microsoft Excel. Si può però creare un'estensione personalizzata del framework dei test codificati dell'interfaccia utente che supporti l'interfaccia utente specifica sfruttando l'estendibilità del framework stesso.

![Architettura di test dell'interfaccia utente](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Estensione di esempio per il test di Microsoft Excel

Questo [post di blog](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) contiene un collegamento a un'[estensione di esempio](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) per il framework di test codificato dell'interfaccia utente. È anche possibile visualizzare l'intera [serie di post di blog per l'estendibilità dei test codificati dell'interfaccia utente](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/).

> [!NOTE]
> L'esempio è concepito per Microsoft Excel 2010. Può funzionare o meno con altre versioni di Excel.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Procedure consigliate per i test codificati dell'interfaccia utente](../test/best-practices-for-coded-ui-tests.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)