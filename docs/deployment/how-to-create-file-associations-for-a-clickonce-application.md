---
title: Creare associazioni di file (ClickOnce app)
description: Informazioni su come associare un'ClickOnce a una o più estensioni di file, in modo che l'applicazione si avvia quando l'utente apre un file di questo tipo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: f05e61bc44f8a2db5f4a498df369131cc728df0a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127961"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedura: Creare associazioni di file per un'applicazione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Le applicazioni possono essere associate a una o più estensioni di file, in modo che l'applicazione verrà avviata automaticamente quando l'utente apre un file di questi tipi. L'aggiunta del supporto dell'estensione di file a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione è semplice.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Per creare associazioni di file per un'ClickOnce applicazione

1. Creare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione normalmente o usare l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esistente.

2. Aprire il manifesto dell'applicazione con un editor di testo o XML, ad esempio Blocco note.

3. Trovare l'elemento `assembly`. Per altre informazioni, vedere [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).

4. Aggiungere un elemento come figlio `assembly` `fileAssociation` dell'elemento . `fileAssociation`L'elemento ha quattro attributi:

   - `extension`: estensione del nome file da associare all'applicazione.

   - `description`: descrizione del tipo di file, che verrà visualizzata nella Windows shell.

   - `progid`: stringa che identifica in modo univoco il tipo di file, per contrassegnarlo nel Registro di sistema.

   - `defaultIcon`: icona da usare per questo tipo di file. L'icona deve essere aggiunta come risorsa file nel manifesto dell'applicazione. Per altre informazioni, vedere [Procedura: Includere un file di dati in un'ClickOnce applicazione](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Per un esempio degli `file` elementi e , vedere `fileAssociation` [ \<fileAssociation> Element](../deployment/fileassociation-element-clickonce-application.md).

5. Se si desidera associare più di un tipo di file all'applicazione, aggiungere altri `fileAssociation` elementi. Si noti che `progid` l'attributo deve essere diverso per ognuno.

6. Dopo aver completato l'operazione con il manifesto dell'applicazione, firmare nuovamente il manifesto. È possibile eseguire questa operazione dalla riga di comando *usandoMage.exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Vedi anche
- [\<fileAssociation> Elemento](../deployment/fileassociation-element-clickonce-application.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)