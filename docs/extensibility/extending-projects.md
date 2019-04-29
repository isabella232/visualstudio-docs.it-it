---
title: Estensione di progetti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d31da41e3be73f4e2e036841bfc1d96f4476e856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912805"
---
# <a name="extend-projects"></a>Estendere i progetti
Progetti e soluzioni sono i modi in cui che Visual Studio consente di organizzare i file di codice e risorse in unità di compilazione e distribuzione. È possibile trovare altre informazioni sui progetti in [progetti (Visual Studio SDK)](../extensibility/extending-projects.md).

 È possibile creare i tipi di progetto con Visual Studio SDK e il Framework di pacchetto gestito per progetti, che è possibile scaricare all'indirizzo [Framework di pacchetto gestito per progetti](https://github.com/tunnelvisionlabs/MPFProj10). Per comprendere come vengono implementati i progetti personalizzati, vedere [nuova generazione progetto: Dietro le quinte, parte 1](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nuova generazione progetto: Dietro le quinte, parte 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Negli argomenti di questa sezione viene descritto come creare progetti personalizzati e come gestire diversi tipi di soluzione di Visual Studio.

## <a name="in-this-section"></a>Contenuto della sezione
- [Creare un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) viene descritto come creare un sistema di progetto personalizzato.

- [Creare un sistema di progetto di base, parte 2](../extensibility/creating-a-basic-project-system-part-2.md) viene descritto come creare un sistema di progetto personalizzato.

- [Salvare i dati nei file di progetto](../extensibility/saving-data-in-project-files.md) indica come aggiungere al progetto (<em>.</em> proj *) i file.

- [Verificare i sottotipi di un progetto in fase di esecuzione](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) viene spiegato come verificare il sottotipo di un progetto in fase di esecuzione.

- [Aggiungere e rimuovere le pagine delle proprietà](../extensibility/adding-and-removing-property-pages.md) viene illustrato come personalizzare le pagine delle proprietà per un progetto personalizzato.

- [Aggiungere un attributo a un elemento di progetto](../extensibility/adding-an-attribute-to-a-project-item.md) viene illustrato come aggiungere un attributo a un elemento di progetto personalizzato.

- [Rendere permanente la proprietà di un elemento di progetto](../extensibility/persisting-the-property-of-a-project-item.md) spiega come rendere persistenti le proprietà di un elemento di progetto personalizzato.

- [Gestire i progetti Windows universali](../extensibility/managing-universal-windows-projects.md) viene illustrato come gestire i progetti UWP.