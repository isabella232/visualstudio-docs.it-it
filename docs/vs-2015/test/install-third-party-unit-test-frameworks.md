---
title: Installare framework di unit test di terze parti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bd087dc0b06cbf8ffe4c08f84d819e8ef1c2f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660519"
---
# <a name="install-third-party-unit-test-frameworks"></a>Installare framework di unit test di terze parti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esplora test di Visual Studio può eseguire qualsiasi framework di unit test che ha sviluppato un'interfaccia di adattatore per Esplora test. Il programma di installazione del framework installa i file binari e aggiunge modelli di progetto di Visual Studio per i linguaggi supportati. Quando si crea un progetto con il modello, il framework viene registrato con Esplora test. Una soluzione di Visual Studio può includere progetti unit test che usano diversi framework e fanno riferimento a diversi linguaggi. Esplora test li esegue tutti.

 **Requirements**

- Visual Studio Enterprise, Visual Studio Professional

## <a name="acquiring-third-party-frameworks"></a>Acquisizione di framework di terze parti
 È possibile scaricare e installare molti framework di unit test di terze parti usando Gestione estensioni di Visual Studio o da Visual Studio Gallery nel sito Web MSDN. I framework sono disponibili per il download anche da altri siti, ad esempio il sito Web specifico del framework.

### <a name="installing-from-visual-studio"></a>Installazione da Visual Studio

1. Scegliere **Strumenti** nel menu standard e quindi **Estensioni e aggiornamenti**.

2. Espandere **Online**, **Visual Studio Gallery**, **Strumenti**. Scegliere **Test**.

3. Cercare il framework nell'elenco.

4. Selezionare il framework e scegliere **Download**.

   Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Installazione dal Web
 Se si conosce il framework che si vuole usare:

1. Aprire [Visual Studio Marketplace](https://marketplace.visualstudio.com).

2. Digitare il nome del framework nella casella **Trova**.

3. Scegliere il framework dall'elenco di risultati per passare alla pagina di Visual Studio Gallery per lo strumento.

   Per sfogliare un elenco di framework e di altri strumenti di test:

4. Aprire [Visual Studio Marketplace](https://marketplace.visualstudio.com).

5. Scegliere **Sfoglia**.

6. Nell'elenco **Categoria** espandere il nodo **Strumenti** e quindi scegliere **Test**.

7. Scegliere un framework dall'elenco di risultati per passare alla pagina di Visual Studio Gallery per lo strumento.

## <a name="see-also"></a>Vedere anche
 [Eseguire unit test del codice](../test/unit-test-your-code.md)
