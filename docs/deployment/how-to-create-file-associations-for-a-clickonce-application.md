---
title: "Procedura: Creare associazioni di file per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0526351d2b3e2c223aacbe0e58d9ee39bd1b19c4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924551"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedura: Creare associazioni di file per un'applicazione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni possono essere associate a una o più estensioni di file, in modo che l'applicazione venga avviata automaticamente quando l'utente apre un file di tali tipi. L'aggiunta del supporto dell'estensione del [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nome di file a un'applicazione è semplice.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Per creare associazioni di file per un'applicazione ClickOnce

1. Creare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione normalmente oppure usare l'applicazione esistente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. Aprire il manifesto dell'applicazione con un editor di testo o XML, ad esempio Blocco note.

3. Trovare l'elemento `assembly` . Per altre informazioni, vedere [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).

4. Aggiungere un `assembly` `fileAssociation` elemento come figlio dell'elemento. L' `fileAssociation` elemento ha quattro attributi:

   - `extension`: Estensione del nome di file che si desidera associare all'applicazione.

   - `description`: Descrizione del tipo di file, che verrà visualizzato nella shell di Windows.

   - `progid`: Stringa che identifica in modo univoco il tipo di file, per contrassegnarla nel registro di sistema.

   - `defaultIcon`: Icona da usare per questo tipo di file. L'icona deve essere aggiunta come risorsa file nel manifesto dell'applicazione. Per altre informazioni, vedere [Procedura: Includere un file di dati in un'applicazione ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Per un esempio degli `file` elementi e `fileAssociation` , vedere [ \<elemento fileAssociation >](../deployment/fileassociation-element-clickonce-application.md).

5. Se si desidera associare più di un tipo di file all'applicazione, aggiungere altri `fileAssociation` elementi. Si noti che `progid` l'attributo deve essere diverso per ogni.

6. Una volta terminato il manifesto dell'applicazione, firmare nuovamente il manifesto. È possibile eseguire questa operazione dalla riga di comando tramite *Mage. exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Vedere anche
- [\<elemento fileAssociation >](../deployment/fileassociation-element-clickonce-application.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)