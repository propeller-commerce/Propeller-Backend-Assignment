# 🚀 Propeller Backend Assignment

This backend assignments main goal is to test your ability to build a simple test `e-commerce` `GraphQL` `API` using `JS/TS` and `Node.js` (other languages are fine as well!).

The assignment is divided into three parts:

    1. build a GraphQL api for serving `products`
    2. build a GraphQL api for serving `images`
    3. connect the two APIs together using GraphQL federation or schema stitching

Main goal is to provide a single endpoint like `http://localhost/graphql` that will serve both `products` and `images` data.

This task should take you no more than a full work day to complete (please try to keep it within this time frame)

Please divide your time as it seems fit and try to submit the assignment in 3-4 days max.

## Description

We are building a simple `e-commerce` API that will serve `products` and `images`.

The API will be used by multiple frontend applications that will display the `products` and `images`.

The API should be able to serve the data in a way that is easy to consume by the frontend applications.

You are free to use any libraries or frameworks to achieve the goal.

We are using `NestJS` and `TypeORM` in our projects so it would be nice if you could use them as well.

But if you are more comfortable with other libraries or frameworks feel free to use them.

Also feel free to use any database and ORM of your choice.

Please refer to the [Bonus Points](#bonus-points) and [Above and Beyond](#above-and-beyond) sections for more ideas on how to increase your score :)

## Queries and Mutations to implement

```graphql

type Query {
    products: [Product]
    product(id: ID!): Product
    images: [Image]
    image(id: ID!): Image
}

type Mutation {
    createProduct(input: CreateProductInput!): Product
    updateProduct(id: ID!, input: UpdateProductInput!): Product
    deleteProduct(id: ID!): Product
    createImage(input: CreateImageInput!): Image
    updateImage(id: ID!, input: UpdateImageInput!): Image
    deleteImage(id: ID!): Image
    linkImageToProduct(productId: ID!, imageId: ID!): Product
    unlinkImageFromProduct(productId: ID!, imageId: ID!): Product
}
```

## Basic Minimal Models

### Product

Every product must has a `name`, `description`, `sku`, `price` and `status`.

A product can have 0 or multiple images.

```ts
{
    id: string | number,
    name: string,
    description: string,
    sku: string,
    status: 'active' | 'inactive' | 'out-of-stock', // default: 'active'
    price: number,
    // images?: [Image]
}
```

### Image

Every image must have a `url`, `name`, `alt` and `priority`.

An image can be associated with a product.

```ts
{
    id: string | number,
    url: string,
    name: string,
    alt: string,
    priority: number, // default: 1000
    productId?: string | number
    // product: Product
}
```

`NOTE:` please assume that the `url` is a valid url to an image hosted on a CDN or a file server.
[For example](https://images.unsplash.com/photo-1615789591457-74a63395c990?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80)

## Minimal Requirements

1. Implemented majority of the required `queries` and `mutations`
2. Use GraphQL federation (Apollo federation v2) or schema stitching
3. Minimal local working example
4. At least some minimal filtering options on the queries

## Bonus Points

1. Implemented all the required queries and mutations
2. Use `TypeScript`
3. Use `NestJS`
4. Use GraphQL federation (Apollo federation v2)
5. Use `TypeORM` with `MySQL` (provide DB schemas, migrations and seeders)
6. Advanced/multiple filtering options on the queries
7. Create full `Dockerfile` and `docker-compose.yml` for running the `APIs` and `DB` locally
8. Implement `CI/CD` pipeline for test, build and deployment of the `APIs` (Gitlab,Github Actions, etc.)
9. Deploy the `APIs` to a cloud provider of your choice (non mandatory, example setup is fine as well)

## Above and Beyond

Given the time constraint of this assignment we don't expect anyone to submit fill blown production ready code.
But if you have some spare time and want to go above and beyond here are some ideas:

    1. some unit tests
    2. extra items that you think are important for a production ready API
    3. simple frontend showcasing the new API usage

## Submission

When you have finished the assignment please submit a link to your repo to the person who sent you this assignment.

## Good luck
