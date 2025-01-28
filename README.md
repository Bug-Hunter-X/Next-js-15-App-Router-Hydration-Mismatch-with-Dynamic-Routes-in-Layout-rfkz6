# Next.js 15 App Router Hydration Mismatch Bug

This repository demonstrates a hydration mismatch bug in Next.js 15's App Router when using dynamic routes and data fetching within a layout component. The bug occurs when the layout component attempts to access route parameters before the data fetching has completed, leading to a hydration mismatch error during client-side navigation.

## Bug Description

The bug arises from accessing route parameters in the layout component's `getServerSideProps` or equivalent before the data is fetched. If the data fetching relies on these parameters, it results in an error during client-side navigation. This is because the initial render (on the server) might not have the parameters available, yet the layout tries to use them before the fetch completes.

## Solution

The solution involves ensuring that data fetching is conditioned on the availability of the parameters and that the component renders gracefully during this initial render.