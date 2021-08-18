---
title: Estensione dei progetti | Microsoft Docs
description: Informazioni su come creare tipi di progetto personalizzati in Visual Studio SDK e su come gestire diversi tipi di Visual Studio soluzioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a6d7d93f4cd805db5bd161517c0af9a862457edb47aff912e6eab0afa7de0dbf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448351"
---
# <a name="extend-projects"></a>Estendere i progetti
I progetti e le soluzioni sono il modo in cui Visual Studio i file di codice e di risorse in unità di compilazione e distribuzione. Altre informazioni sui progetti sono disponibili in [Progetti (Visual Studio SDK).](../extensibility/extending-projects.md)

 È possibile creare tipi di progetto personalizzati con Visual Studio SDK e Managed Package Framework for Projects, che è possibile scaricare in [Managed Package Framework for Projects](https://github.com/tunnelvisionlabs/MPFProj10). Per comprendere come vengono implementati i progetti personalizzati, vedere New [project generation: Under the hood,](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) part one e [New project generation: Under the hood, part two](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Negli argomenti di questa sezione viene descritto come creare progetti personalizzati e come gestire diversi tipi di Visual Studio soluzione.

## <a name="in-this-section"></a>Contenuto della sezione
- [Creare un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) Viene descritto come creare un sistema di progetto personalizzato.

- [Creare un sistema di progetto di base, parte 2](../extensibility/creating-a-basic-project-system-part-2.md) Viene descritto come creare un sistema di progetto personalizzato.

- [Salvare i dati nei file di progetto](../extensibility/saving-data-in-project-files.md) Viene illustrato come aggiungere al progetto (<em>.</em> file proj*).

- [Verificare i sottotipi di un progetto in fase di esecuzione](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Viene illustrato come verificare il sottotipo di un progetto in fase di esecuzione.

- [Aggiungere e rimuovere pagine delle proprietà](../extensibility/adding-and-removing-property-pages.md) Viene illustrato come personalizzare le pagine delle proprietà per il progetto personalizzato.

- [Aggiungere un attributo a un elemento di progetto](../extensibility/adding-an-attribute-to-a-project-item.md) Viene illustrato come aggiungere un attributo a un elemento di progetto personalizzato.

- [Rendere persistente la proprietà di un elemento di progetto](../extensibility/persisting-the-property-of-a-project-item.md) Viene illustrato come rendere persistenti le proprietà di un elemento di progetto personalizzato.

- [Gestire i progetti Windows universali](../extensibility/managing-universal-windows-projects.md) Viene illustrato come gestire i progetti universali.
