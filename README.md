# Make Real

Use this repo as a template to create Make Real style apps like
https://makereal.tldraw.com. To get started:

1. Use the template and clone your new repo to your computer
2. Run `npm install` to install dependencies
3. Get an OpenAI API key from https://platform.openai.com/api-keys. Make sure
   you are at least a
   [Tier 1](https://platform.openai.com/docs/guides/rate-limits/usage-tiers) API
   user, which means you have access to GPT-4 Vision. You can check your tier on
   the [OpenAI API Limits](https://platform.openai.com/account/limits).
4. Create a `.env.local` file that contains `OPENAI_API_KEY=your api key here`
5. Run `npm run dev`
6. Open http://localhost:3000 and make some stuff real!

## How it works

Make Real is built on [tldraw](tldraw.dev), a very good React library for
creating whiteboards and other infinite canvas experiences.

Users can use tldraw's tools to sketch out a mock for a piece of UI. When
they're ready, they can select their drawing, and press the Make Real button.
We'll capture an image of their sketch, and send it to
[OpenAI's GPT-4V](https://platform.openai.com/docs/guides/vision) along with
instructions to turn it into a HTML file.

We take the HTML response and add it to a tldraw
[custom shape](https://tldraw.dev/docs/shapes#Custom-shapes). The custom shape
shows the response in an iframe that the user can interact with. If the user
wants to iterate on the response, they can annotate the response, select it &
the annotations, and press 'Make Real' again to repeat the process with the last
response as a starting point.

## To make changes

To change how Make Real works, start from the [`makeReal()`](./app/makeReal.tsx)
function. From there, you can change the prompt that gets sent to gpt-4.

If you'd like Make Real to create something other than HTML, you'll need to
either update the [`ResponseShape`](./app/ResponseShape/ResponseShape.tsx) to
display something different, or use one of tldraw's built-in shapes like image
or text.
