---
UID: NN:strmif.IAMPushSource
title: IAMPushSource (strmif.h)
description: The IAMPushSource interface synchronizes a filter graph that renders a live source.
helpviewer_keywords: ["IAMPushSource","IAMPushSource interface [DirectShow]","IAMPushSource interface [DirectShow]","described","IAMPushSourceInterface","dshow.iampushsource","strmif/IAMPushSource"]
old-location: dshow\iampushsource.htm
tech.root: dshow
ms.assetid: 5ab294a8-f250-405c-a589-68998bc04cdf
ms.date: 12/05/2018
ms.keywords: IAMPushSource, IAMPushSource interface [DirectShow], IAMPushSource interface [DirectShow],described, IAMPushSourceInterface, dshow.iampushsource, strmif/IAMPushSource
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
 - IAMPushSource
 - strmif/IAMPushSource
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
 - IAMPushSource
---

# IAMPushSource interface


## -description

The <code>IAMPushSource</code> interface synchronizes a filter graph that renders a live source. A live source is a source that streams data in real time, such as a capture device or a network broadcast.

Source filters that stream live data should expose this interface on their output pins. Generally, applications should not call the methods on this interface; instead, use the <a href="/windows/desktop/api/strmif/nn-strmif-iamgraphstreams">IAMGraphStreams</a> interface.

## -inheritance

The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IAMPushSource</b> interface inherits from <a href="/windows/desktop/api/strmif/nn-strmif-iamlatency">IAMLatency</a>. <b>IAMPushSource</b> also has these types of members:

## -remarks

The Filter Graph Manager uses the methods on this interface to address two problems that commonly occur when rendering live sources:

<ul>
<li>Latency: When a filter graph includes more than one live source, the sources often have different latencies, which can cause them to be out of sync. For example, if audio capture has a longer latency time than video capture, the audio will lag behind the video unless the graph compensates for the difference.</li>
<li>Rate Matching: When a renderer filter is connected to a live source, it must adjust its data consumption rate to match the source filter's production rate. Otherwise, there might be gaps in the data (if the renderer runs faster than the source) or data might get dropped (if the source runs faster).</li>
</ul>
To correct for latency, the filter graph calls <a href="/windows/desktop/api/strmif/nf-strmif-iamlatency-getlatency">IAMLatency::GetLatency</a> on each output pin that exposes the <code>IAMPushSource</code> interface, and determines the maximum latency in the graph. It then calls <a href="/windows/desktop/api/strmif/nf-strmif-iampushsource-setstreamoffset">IAMPushSource::SetStreamOffset</a> on any filters with less than the maximum latency, so that they will adjust the time stamps they generate by the correct offset.

To perform rate matching, the filter graph needs to determine whether the renderer filter can match clock rates with the source filter. The <a href="/windows/desktop/api/strmif/nf-strmif-iampushsource-getpushsourceflags">IAMPushSource::GetPushSourceFlags</a> method returns a set of flags indicating whether it is safe for the renderer to match rates with the source.

These issues do not affect capturing to a file. The <a href="/windows/desktop/DirectShow/file-writer-filter">File Writer</a> filter relies on time stamps on the incoming samples to write the file correctly; the streams are then synchronized during playback. As for rate matching, the data is always written to the file as fast as possible.

## -see-also

<a href="/windows/desktop/api/strmif/nn-strmif-iamlatency">IAMLatency</a>
