---
UID: NN:strmif.IEnumStreamIdMap
title: IEnumStreamIdMap (strmif.h)
description: The IEnumStreamIdMap interface is implemented on a standard COM collection of Stream ID maps that have been created by the MPEG-2 Demultiplexer's IMPEG2StreamIdMap::MapStreamId method.
helpviewer_keywords: ["IEnumStreamIdMap","IEnumStreamIdMap interface [DirectShow]","IEnumStreamIdMap interface [DirectShow]","described","IEnumStreamIdMapInterface","dshow.ienumstreamidmap","strmif/IEnumStreamIdMap"]
old-location: dshow\ienumstreamidmap.htm
tech.root: dshow
ms.assetid: 8bca9255-2bc8-408b-9127-e3fe050fcf01
ms.date: 12/05/2018
ms.keywords: IEnumStreamIdMap, IEnumStreamIdMap interface [DirectShow], IEnumStreamIdMap interface [DirectShow],described, IEnumStreamIdMapInterface, dshow.ienumstreamidmap, strmif/IEnumStreamIdMap
req.header: strmif.h
req.include-header: Dshow.h
req.target-type: Windows
req.target-min-winverclnt: Windows XP [desktop apps only]
req.target-min-winversvr: Windows Server 2003 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Strmiids.lib
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - IEnumStreamIdMap
 - strmif/IEnumStreamIdMap
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - Strmiids.lib
 - Strmiids.dll
api_name:
 - IEnumStreamIdMap
---

# IEnumStreamIdMap interface


## -description

The <code>IEnumStreamIdMap</code> interface is implemented on a standard COM collection of Stream ID maps that have been created by the <a href="/windows/desktop/DirectShow/mpeg-2-demultiplexer">MPEG-2 Demultiplexer</a>'s <a href="/windows/desktop/api/strmif/nf-strmif-impeg2streamidmap-mapstreamid">IMPEG2StreamIdMap::MapStreamId</a> method. To obtain a pointer to this interface, use the <a href="/windows/desktop/api/strmif/nf-strmif-impeg2streamidmap-enumstreamidmap">IMPEG2StreamIdMap::EnumStreamIdMap</a> method. Typically, an output pin will never have more than one stream ID mapped to it at any given time. This collection represents a snapshot of the Stream IDs mapped at the time the collection is created. The collection is not updated automatically.

## -inheritance

The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IEnumStreamIdMap</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>IEnumStreamIdMap</b> also has these types of members:

