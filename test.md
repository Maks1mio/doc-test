# Markdown Cheat Sheet

Thanks for visiting [The Markdown Guide](https://www.markdownguide.org)!

This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax) and [extended syntax](https://www.markdownguide.org/extended-syntax).

## Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

### Heading

# H1
## H2
### H3

### Bold

**bold text**

### Italic

*italicized text*

### Blockquote

> blockquote

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

- First item
- Second item
- Third item

### Code

`code`

### Horizontal Rule

---

### Link

[Markdown Guide](https://www.markdownguide.org)

### Image

![alt text](https://www.markdownguide.org/assets/images/tux.png)

## Extended Syntax

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

### Table

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

### Fenced Code Block

<div class="code-container">
    <textarea style="display: none;" disabled type="text"
        id="text-to-copy-1">Sprite,Foreground,<origin>,"<filepath>",<x>,<y></y></textarea>
    <div class="svg-icon"><img src="lib/svg/laboratory/browser-code.svg" alt=""></div>
    <pre><code class="language-csharp" data-input-id="text-to-copy-1"></code></pre>
    <button class="copy-button" data-input-id="text-to-copy-1" type="button"><img
            src="lib/svg/laboratory/content-copy.svg" alt=""></button>
</div>

<div class="code-container">
<textarea style="display: none;" disabled type="text" id="text-to-copy-2">
// Unity C# reference source
// Copyright (c) Unity Technologies. For terms of use, see
// https://unity3d.com/legal/licenses/Unity_Reference_Only_License

using System;
using UnityEngine;
using UnityEngine.Bindings;
using UnityEngine.Scripting;
using UnityEngine.Playables;

namespace UnityEngine.Animations
{
    [NativeHeader("Modules/Animation/ScriptBindings/AnimationMotionXToDeltaPlayable.bindings.h")]
    [StaticAccessor("AnimationMotionXToDeltaPlayableBindings", StaticAccessorType.DoubleColon)]
    [RequiredByNativeCode]
    internal struct AnimationMotionXToDeltaPlayable : IPlayable, IEquatable<AnimationMotionXToDeltaPlayable>
    {
        PlayableHandle m_Handle;

        static readonly AnimationMotionXToDeltaPlayable m_NullPlayable = new AnimationMotionXToDeltaPlayable(PlayableHandle.Null);
        public static AnimationMotionXToDeltaPlayable Null { get { return m_NullPlayable; } }

        public static AnimationMotionXToDeltaPlayable Create(PlayableGraph graph)
        {
            var handle = CreateHandle(graph);
            return new AnimationMotionXToDeltaPlayable(handle);
        }

        private static PlayableHandle CreateHandle(PlayableGraph graph)
        {
            PlayableHandle handle = PlayableHandle.Null;
            if (!CreateHandleInternal(graph, ref handle))
                return PlayableHandle.Null;

            handle.SetInputCount(1);
            return handle;
        }

        private AnimationMotionXToDeltaPlayable(PlayableHandle handle)
        {
            if (handle.IsValid())
            {
                if (!handle.IsPlayableOfType<AnimationMotionXToDeltaPlayable>())
                    throw new InvalidCastException("Can't set handle: the playable is not an AnimationMotionXToDeltaPlayable.");
            }

            m_Handle = handle;
        }

        public PlayableHandle GetHandle()
        {
            return m_Handle;
        }

        public static implicit operator Playable(AnimationMotionXToDeltaPlayable playable)
        {
            return new Playable(playable.GetHandle());
        }

        public static explicit operator AnimationMotionXToDeltaPlayable(Playable playable)
        {
            return new AnimationMotionXToDeltaPlayable(playable.GetHandle());
        }

        public bool Equals(AnimationMotionXToDeltaPlayable other)
        {
            return GetHandle() == other.GetHandle();
        }

        public bool IsAbsoluteMotion()
        {
            return IsAbsoluteMotionInternal(ref m_Handle);
        }

        public void SetAbsoluteMotion(bool value)
        {
            SetAbsoluteMotionInternal(ref m_Handle, value);
        }

        // Bindings methods.
        [NativeThrows]
        extern private static bool CreateHandleInternal(PlayableGraph graph, ref PlayableHandle handle);
        [NativeThrows]
        extern static private bool IsAbsoluteMotionInternal(ref PlayableHandle handle);
        [NativeThrows]
        extern static private void SetAbsoluteMotionInternal(ref PlayableHandle handle, bool value);
    }
}
</textarea>
<div class="svg-icon"><img src="lib/svg/laboratory/browser-code.svg" alt=""></div>
<pre><code class="language-csharp" data-input-id="text-to-copy-2"></code></pre>
<button class="copy-button" data-input-id="text-to-copy-2" type="button"><img src="lib/svg/laboratory/content-copy.svg" alt=""></button>
</div>

### Footnote

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

### Heading ID

### My Great Heading {#custom-id}

### Definition List

term
: definition

### Strikethrough

~~The world is flat.~~

### Task List

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

### Emoji

That is so funny! :joy:

(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))

### Highlight

I need to highlight these ==very important words==.

### Subscript

H~2~O

### Superscript

X^2^
