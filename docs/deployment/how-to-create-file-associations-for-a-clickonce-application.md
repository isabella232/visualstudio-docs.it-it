---
title: "Procedura: creare associazioni di File per un'applicazione ClickOnce | Microsoft Docs"
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
ms.openlocfilehash: 15d9b81bd342ccd8a5ee3377323e140ab1167c10
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633044"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedura: Creare associazioni di file per un'applicazione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni possono essere associate a uno o più estensioni di file, in modo che l'applicazione verrà avviata automaticamente quando l'utente apre un file di tali tipi. Aggiunta di supporto delle estensioni di file a un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è molto semplice.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Per creare associazioni di file per un'applicazione ClickOnce

1. Creare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione in genere, o utilizzare le proprie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.

2. Aprire il manifesto dell'applicazione con un editor di testo o XML, ad esempio Blocco note.

3. Trovare l'elemento `assembly` . Per altre informazioni, vedere [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).

4. Come elemento figlio di `assembly` elemento, aggiungere un `fileAssociation` elemento. Il `fileAssociation` caratterizzato da quattro attributi:

   - `extension`: L'estensione che si desidera associare all'applicazione.

   - `description`: Descrizione del tipo di file, verrà visualizzato nella shell di Windows.

   - `progid`: Stringa che identifica in modo univoco il tipo di file, per contrassegnare quest ' ultimo nel Registro di sistema.

   - `defaultIcon`: Un'icona da usare per questo tipo di file. L'icona deve essere aggiunto come una risorsa di file nel manifesto dell'applicazione. Per altre informazioni, vedere [Procedura: Includere un file di dati in un'applicazione ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Per un esempio del `file` e `fileAssociation` sugli elementi, vedere [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).

5. Se si desidera associare più di un tipo di file all'applicazione, aggiungere altri `fileAssociation` elementi. Si noti che il `progid` deve essere diverso per ogni attributo.

6. Dopo aver completato con il manifesto dell'applicazione, è necessario firmare nuovamente il manifesto. È possibile farlo dalla riga di comando usando *Mage.exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)

## <a name="see-also"></a>Vedere anche
- [\<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)