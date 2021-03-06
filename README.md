# Yesod markdown

[![Build Status](https://travis-ci.org/pbrisbin/yesod-markdown.svg?branch=master)](https://travis-ci.org/pbrisbin/yesod-markdown)

A small wrapper over pandoc's powerful `Markdown -> Html` support with usage
tailored for Yesod.

This is a fork and continuation of a package originally by Alexander Dunlap.

Differences include:

1. Updated to compile with newer dependencies
2. Removed `Yesod.Markdown.Macros`
3. Fixed and exported form field settings for `Markdown` fields
4. Uses xss-sanitize by default and provides `*Trusted` functions to skip it

## Usage

```
getPageR :: FilePath -> Handler RepHtml
getPageR fp = do
    content <- liftIO $ fmap markdownToHtml (markdownFromFile fp)

    defaultLayout do
        [shamlet|
            <div class="content">
                #{content}
            |]
```
