---
title: Estendere test codificati dell'interfaccia utente e registrazioni delle azioni
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bc4e500c401c148f9eb01c1dedd56f89ba534df8
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692057"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Estendere test codificati dell'interfaccia utente e registrazioni delle azioni

Il framework di test per i test codificati dell'interfaccia utente e le registrazioni delle azioni non supportano tutte le interfacce utente disponibili, e quindi potrebbero non supportare l'interfaccia utente specifica di cui eseguire il test. Ad esempio, non si può creare immediatamente un test codificato dell'interfaccia utente o una registrazione delle azioni per un foglio di calcolo di Microsoft Excel. Si può però creare un'estensione personalizzata del framework dei test codificati dell'interfaccia utente che supporti l'interfaccia utente specifica sfruttando l'estendibilità del framework stesso.

![Architettura di test dell'interfaccia utente](../test/media/ui_testarch.png)

## <a name="sample-extension-to-test-microsoft-excel"></a>Estensione di esempio per il test di Microsoft Excel

Questo [post di blog](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) contiene un collegamento a un'[estensione di esempio](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) per il framework di test codificato dell'interfaccia utente. È anche possibile visualizzare l'intera [serie di post di blog per l'estendibilità dei test codificati dell'interfaccia utente](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/).

> [!NOTE]
> L'esempio è concepito per Microsoft Excel 2010. Può funzionare o meno con altre versioni di Excel.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Procedure consigliate per i test codificati dell'interfaccia utente](../test/best-practices-for-coded-ui-tests.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)