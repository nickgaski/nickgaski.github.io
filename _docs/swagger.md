---
swagger: '2.0'
layout: swagger
info:
  description: Manages the networks
  version: 1.0.0
  title: Consortia (Network Manager)
host: api.photic.io
basePath: /v1
tags:
  - name: Consortia
  - name: Invitations & Memberships
  - name: Environments
  - name: Nodes
schemes:
  - http
  - https
consumes:
  - application/json
produces:
  - application/json
security:
  - jwt_token_header: []
  - jwt_token_query: []
parameters:
  includeChildren:
    name: includeChildren
    in: query
    type: boolean
  consortia_id:
    name: consortia_id
    in: path
    type: string
    required: true
  invitation_id:
    name: invitation_id
    in: path
    type: string
    required: true
  membership_id:
    name: membership_id
    in: path
    type: string
    required: true
  environment_id:
    name: environment_id
    in: path
    type: string
    required: true
  node_id:
    name: node_id
    in: path
    type: string
    required: true
  policy_id:
    name: policy_id
    in: path
    type: string
    required: true
paths:
  /consortia:
    get:
      tags:
        - Consortia
      parameters:
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve consortia available to user
          schema:
            type: array
            items:
              $ref: '#/definitions/Consortia'
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    post:
      tags:
        - Consortia
      parameters:
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Consortia'
      responses:
        '201':
          description: Created consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Consortia'
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}':
    get:
      tags:
        - Consortia
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve consortia
          schema:
            $ref: '#/definitions/Consortia'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    put:
      tags:
        - Consortia
      parameters:
        - $ref: '#/parameters/consortia_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Consortia'
      responses:
        '200':
          description: Updated consortia
          schema:
            $ref: '#/definitions/Consortia'
        '201':
          description: Created consortia
          schema:
            $ref: '#/definitions/Consortia'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    patch:
      tags:
        - Consortia
      parameters:
        - $ref: '#/parameters/consortia_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Consortia'
      responses:
        '200':
          description: Updated consortia
          schema:
            $ref: '#/definitions/Consortia'
        '201':
          description: Created consortia
          schema:
            $ref: '#/definitions/Consortia'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    delete:
      tags:
        - Consortia
      parameters:
        - $ref: '#/parameters/consortia_id'
      responses:
        '204':
          description: Retrieve consortia
          schema:
            $ref: '#/definitions/Consortia'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/invitations':
    get:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve invitations to join the consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Invitation'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    post:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Invitation'
      responses:
        '200':
          description: Create invitation for consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Invitation'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/invitations/{invitation_id}':
    get:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/invitation_id'
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve invitation for consortia
          schema:
            $ref: '#/definitions/Invitation'
        '404':
          description: Could not find Invitation
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    put:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/invitation_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Invitation'
      responses:
        '200':
          description: Updated invitation for consortia
          schema:
            $ref: '#/definitions/Invitation'
        '201':
          description: Created invitation for consortia
          schema:
            $ref: '#/definitions/Invitation'
        '404':
          description: Could not find Invitation
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    patch:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/invitation_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Invitation'
      responses:
        '200':
          description: Updated invitation for consortia
          schema:
            $ref: '#/definitions/Invitation'
        '201':
          description: Created invitation for consortia
          schema:
            $ref: '#/definitions/Invitation'
        '404':
          description: Could not find Invitation
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    delete:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/invitation_id'
      responses:
        '204':
          description: Deleted invitation for consortia
          schema:
            $ref: '#/definitions/Invitation'
        '404':
          description: Could not find Invitation
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/memberships':
    get:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve memberships for consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Membership'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    post:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Membership'
      responses:
        '200':
          description: Create membership for consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Membership'
        '404':
          description: Could not find Consortia
  '/consortia/{consortia_id}/memberships/{membership_id}':
    get:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/membership_id'
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve membership for consortia
          schema:
            $ref: '#/definitions/Membership'
        '404':
          description: Could not find Membership
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    put:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/membership_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Membership'
      responses:
        '200':
          description: Updated membership for consortia
          schema:
            $ref: '#/definitions/Membership'
        '201':
          description: Created membership for consortia
          schema:
            $ref: '#/definitions/Membership'
        '404':
          description: Could not find Membership
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    patch:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/membership_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Membership'
      responses:
        '200':
          description: Updated membership for consortia
          schema:
            $ref: '#/definitions/Membership'
        '201':
          description: Created membership for consortia
          schema:
            $ref: '#/definitions/Membership'
        '404':
          description: Could not find Membership
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    delete:
      tags:
        - Invitations & Memberships
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/membership_id'
      responses:
        '204':
          description: Deleted membership for consortia
          schema:
            $ref: '#/definitions/Membership'
        '404':
          description: Could not find Membership
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments':
    get:
      tags:
        - Environments
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve environments for consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Environment'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    post:
      tags:
        - Environments
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Environment'
      responses:
        '200':
          description: Create environment for consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Environment'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments/{environment_id}':
    get:
      tags:
        - Environments
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
        - $ref: '#/parameters/includeChildren'
      responses:
        '200':
          description: Retrieve environment for consortia
          schema:
            $ref: '#/definitions/Environment'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    put:
      tags:
        - Environments
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Environment'
      responses:
        '200':
          description: Updated environment for consortia
          schema:
            $ref: '#/definitions/Environment'
        '201':
          description: Created environment for consortia
          schema:
            $ref: '#/definitions/Environment'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    patch:
      tags:
        - Environments
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Environment'
      responses:
        '200':
          description: Updated environment for consortia
          schema:
            $ref: '#/definitions/Environment'
        '201':
          description: Created environment for consortia
          schema:
            $ref: '#/definitions/Environment'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    delete:
      tags:
        - Environments
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
      responses:
        '204':
          description: Deleted environment for consortia
          schema:
            $ref: '#/definitions/Environment'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments/{environment_id}/nodes':
    get:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
      responses:
        '200':
          description: Retrieve nodes for environment
          schema:
            type: array
            items:
              $ref: '#/definitions/Node'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    post:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Node'
      responses:
        '200':
          description: Create node for environment
          schema:
            type: array
            items:
              $ref: '#/definitions/Node'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments/{environment_id}/nodes/{node_id}':
    get:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
      responses:
        '200':
          description: Retrieve node for consortia
          schema:
            $ref: '#/definitions/Node'
        '404':
          description: Could not find Node
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    put:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Node'
      responses:
        '200':
          description: Updated node for environment
          schema:
            $ref: '#/definitions/Node'
        '201':
          description: Created node for environment
          schema:
            $ref: '#/definitions/Node'
        '404':
          description: Could not find Node
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    patch:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Node'
      responses:
        '200':
          description: Updated node for environment
          schema:
            $ref: '#/definitions/Node'
        '201':
          description: Created node for environment
          schema:
            $ref: '#/definitions/Node'
        '404':
          description: Could not find Node
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    delete:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
      responses:
        '204':
          description: Deleted environment node
          schema:
            $ref: '#/definitions/Node'
        '404':
          description: Could not find Node
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments/{environment_id}/nodes/{node_id}/status':
    get:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
      responses:
        '200':
          description: Retrieve status for node
          schema:
            type: string
        '404':
          description: Could not find Node
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments/{environment_id}/nodes/{node_id}/logs/{log_type}':
    get:
      tags:
        - Nodes
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/node_id'
        - name: log_type
          in: path
          required: true
          type: string
      responses:
        '200':
          description: Retrieve logs of a given type for node
          schema:
            $ref: '#/definitions/Node'
        '404':
          description: Could not find Node
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/policies':
    get:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
      responses:
        '200':
          description: Retrieve policies for consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Policy'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    post:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Policy'
      responses:
        '200':
          description: Create policy for consortia
          schema:
            type: array
            items:
              $ref: '#/definitions/Policy'
        '404':
          description: Could not find Consortia
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments/{environment_id}/policies':
    get:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
      responses:
        '200':
          description: Retrieve policies for environment
          schema:
            type: array
            items:
              $ref: '#/definitions/Policy'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    post:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Policy'
      responses:
        '200':
          description: Create policy for environment
          schema:
            type: array
            items:
              $ref: '#/definitions/Policy'
        '404':
          description: Could not find Environment
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/policies/{policy_id}':
    get:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/policy_id'
      responses:
        '200':
          description: Retrieve policy for consortia
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    put:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/policy_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Policy'
      responses:
        '200':
          description: Updated policy for consortia
          schema:
            $ref: '#/definitions/Policy'
        '201':
          description: Created policy for consortia
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    patch:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/policy_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Policy'
      responses:
        '200':
          description: Updated policy for consortia
          schema:
            $ref: '#/definitions/Policy'
        '201':
          description: Created policy for consortia
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    delete:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/policy_id'
      responses:
        '204':
          description: Deleted policy for consortia
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
  '/consortia/{consortia_id}/environments/{environment_id}/policies/{policy_id}':
    get:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/policy_id'
      responses:
        '200':
          description: Retrieve policy for environment
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    put:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/policy_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Policy'
      responses:
        '200':
          description: Updated policy for environment
          schema:
            $ref: '#/definitions/Policy'
        '201':
          description: Created policy for environment
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    patch:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/policy_id'
        - name: body
          in: body
          schema:
            $ref: '#/definitions/Policy'
      responses:
        '200':
          description: Updated policy for environment
          schema:
            $ref: '#/definitions/Policy'
        '201':
          description: Created policy for environment
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
    delete:
      tags:
        - Policy
      parameters:
        - $ref: '#/parameters/consortia_id'
        - $ref: '#/parameters/environment_id'
        - $ref: '#/parameters/policy_id'
      responses:
        '204':
          description: Deleted policy for environment
          schema:
            $ref: '#/definitions/Policy'
        '404':
          description: Could not find Policy
        '500':
          description: Internal error
          schema:
            $ref: '#/definitions/Error'
securityDefinitions:
  jwt_token_header:
    name: Bearer
    type: apiKey
    in: header
  jwt_token_query:
    name: access_token
    type: apiKey
    in: query
definitions:
  Consortia:
    type: object
    properties:
      _id:
        type: string
      name:
        type: string
      root:
        type: string
      description:
        type: string
      state:
        type: string
        enum: [setup, live]
      mode:
        type: string
        enum: [single-account, multi-account]
      memberPolicy:
        $ref: '#/definitions/Policy'
      amendmentPolicy:
        $ref: '#/definitions/Policy'
      lockedPolicies:
        type: array
        items:
          $ref: '#/definitions/Policy'
  Invitation:
    type: object
    required:
      - email
      - org_name
    properties:
      _id:
        type: string
      consortia_id:
        type: string
      createdAt:
        type: string
        format: date
      email:
        type: string
      from:
        type: string
      org_name:
        type: string
      resolved_by:
        type: string
      state:
        type: string
        enum: [sent, accepted, declined, revoked, expired]
      account_id:
        type: string
  Membership:
    type: object
    required:
      - account_id
    properties:
      _id:
        type: string
      consortia_id:
        type: string
      account_id:
        type: string
      state:
        type: string
        enum: [active, inactive]
      minimumNodes:
        type: number
      maximumNodes:
        type: number
  Environment:
    type: object
    properties:
      _id:
        type: string
      consortia_id:
        type: string
      root:
        type: string
      name:
        type: string
      description:
        type: string
      state:
        type: string
        enum: [setup, live]
      mode:
        type: string
        enum: [single-account, multi-account]
      provider:
        type: string
        enum: [quorum]
      consensus_type:
        type: string
        enum: [raft, ibft]
      node_list:
        type: array
        items:
          $ref: '#/definitions/Node'
      memberPolicy:
        $ref: '#/definitions/Policy'
      amendmentPolicy:
        $ref: '#/definitions/Policy'
      lockedPolicies:
        type: array
        items:
          $ref: '#/definitions/Policy'
  Node:
    type: object
    required:
      - account_id
      - state
      - provider
      - consensus_type
    properties:
      _id:
        type: string
      consortia_id:
        type: string
      name:
        type: string
      url:
        type: string
      last_height:
        type: number
      private_address:
        type: string
      account_id:
        type: string
      environment_id:
        type: string
      state:
        type: string
        enum: [initializing, started, stopped, failed]
      provider:
        type: string
        enum: [quorum]
      consensys_type:
        type: string
        enum: [raft, ibft]
      quorum_private_address:
        type: string
  Policy:
    type: object
    required:
      - action
      - expression
    properties:
      _id:
        type: string
      consortia_id:
        type: string
      environment_id:
        type: string
      action:
        type: string
      expression:
        type: string
  Error:
    type: object
    properties:
      errorMessage:
        type: string
---
