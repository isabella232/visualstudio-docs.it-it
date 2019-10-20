---
title: Progettare app di Windows Form
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26ad18da19d5a2e53199b49e7acc024c728be9c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634032"
---
# <a name="windows-forms-designer-overview"></a>Panoramica di Progettazione Windows Form

Progettazione Windows Form in Visual Studio fornisce una soluzione di sviluppo rapida per la creazione di applicazioni basate su Windows Form. Progettazione Windows Form consente di aggiungere facilmente controlli a un form, di disporli e di scrivere il codice per i relativi eventi. Per altre informazioni su Windows Form, vedere [Panoramica di Windows Form](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Funzionalità

Usando la finestra di progettazione è possibile:

- Aggiungere componenti, controlli dati o controlli basati su Windows in un form.

- Fare doppio clic sul form nella finestra di progettazione e scrivere il codice nell'evento `Load` per tale form oppure fare doppio clic su un controllo nel form e scrivere il codice per l'evento predefinito del controllo.

- Modificare la proprietà Text di un controllo selezionando il controllo e digitando un nome.

- Modificare la posizione del controllo selezionato spostandolo con il mouse o i tasti di direzione. Analogamente, modificare la posizione in modo più preciso usando CTRL e i tasti di direzione. Infine, modificare le dimensioni del controllo usando MAIUSC e i tasti di direzione.

- Selezionare più controlli premendo **MAIUSC** o **CTRL** mentre si fa clic. Quando si usa **MAIUSC**+clic, il primo controllo selezionato è il controllo dominante durante l'allineamento o la modifica delle dimensioni. Quando si usa **CTRL**+clic, l'ultimo controllo selezionato è il controllo dominante, quindi il controllo dominante cambia con ogni nuovo controllo aggiunto. In alternativa, è possibile selezionare più controlli trascinando un rettangolo di selezione intorno ai controlli che si vuole selezionare.

> [!NOTE]
> Usare Progettazione Windows Form e non l'editor di risorse per apportare modifiche al file di risorse del form (con estensione *resx*). Se si modifica un file con estensione resx basato su form, verrà visualizzato un avviso che indica che le modifiche apportate nell'editor risorse potrebbero andare perse. Questo perché Progettazione Windows Form genera il file resx.

## <a name="see-also"></a>Vedere anche

- [Panoramica sui Windows Form](/dotnet/framework/winforms/windows-forms-overview)
- [Controlli Windows Form](/dotnet/framework/winforms/controls/)
- [Input dell'utente in Windows Form](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Associare dati in Windows Form](/dotnet/framework/winforms/windows-forms-data-binding)
- [Ottimizzare le app di Windows Form](/dotnet/framework/winforms/advanced/)
- Informazioni di riferimento sull'API <xref:System.Windows.Forms?displayProperty=fullName>