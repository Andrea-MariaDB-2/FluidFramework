## API Report File for "@fluidframework/server-services-client"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import * as api from '@fluidframework/protocol-definitions';
import { AxiosInstance } from 'axios';
import { AxiosRequestConfig } from 'axios';
import { ISequencedDocumentMessage } from '@fluidframework/protocol-definitions';
import { ISnapshotTree } from '@fluidframework/protocol-definitions';
import { ISnapshotTreeEx } from '@fluidframework/protocol-definitions';
import { ISummaryHandle } from '@fluidframework/protocol-definitions';
import { ISummaryTree as ISummaryTree_2 } from '@fluidframework/protocol-definitions';
import { ITokenClaims } from '@fluidframework/protocol-definitions';
import { IUser } from '@fluidframework/protocol-definitions';
import * as resources from '@fluidframework/gitresources';
import { ScopeType } from '@fluidframework/protocol-definitions';
import { SummaryObject } from '@fluidframework/protocol-definitions';

// @public (undocumented)
export class BasicRestWrapper extends RestWrapper {
    constructor(baseurl?: string, defaultQueryString?: Record<string, unknown>, maxBodyLength?: number, maxContentLength?: number, defaultHeaders?: Record<string, unknown>, axios?: AxiosInstance, refreshDefaultQueryString?: () => Record<string, unknown>, refreshDefaultHeaders?: () => Record<string, unknown>, getCorrelationId?: () => string | undefined);
    // (undocumented)
    protected request<T>(requestConfig: AxiosRequestConfig, statusCode: number, canRetry?: boolean): Promise<T>;
}

// @public
export const buildTreePath: (...nodeNames: string[]) => string;

// @public (undocumented)
export const canRead: (scopes: string[]) => boolean;

// @public (undocumented)
export const canSummarize: (scopes: string[]) => boolean;

// @public (undocumented)
export const canWrite: (scopes: string[]) => boolean;

// @public (undocumented)
export const choose: () => string;

// @public
export function convertSummaryTreeToWholeSummaryTree(parentHandle: string | undefined, tree: ISummaryTree, path?: string, rootNodeName?: string): IWholeSummaryTree;

// @public
export function convertWholeFlatSummaryToSnapshotTreeAndBlobs(flatSummary: IWholeFlatSummary): INormalizedWholeSummary;

// @public (undocumented)
export const defaultHash = "00000000";

// @public (undocumented)
export type ExtendedSummaryObject = SummaryObject | IEmbeddedSummaryHandle;

// @public
export function generateToken(tenantId: string, documentId: string, key: string, scopes: ScopeType[], user?: IUser, lifetime?: number, ver?: string): string;

// @public (undocumented)
export function generateUser(): IUser;

// @public (undocumented)
export const getAuthorizationTokenFromCredentials: (credentials: ICredentials) => string;

// @public (undocumented)
export function getNextHash(message: ISequencedDocumentMessage, lastHash: string): string;

// @public (undocumented)
export function getOrCreateRepository(endpoint: string, owner: string, repository: string): Promise<void>;

// @public (undocumented)
export function getRandomName(connector?: string, capitalize?: boolean): string;

// @public (undocumented)
export class GitManager implements IGitManager {
    constructor(historian: IHistorian);
    // (undocumented)
    addBlob(blob: resources.IBlob): void;
    // (undocumented)
    addCommit(commit: resources.ICommit): void;
    // (undocumented)
    addRef(ref: string, sha: string): void;
    // (undocumented)
    addTree(tree: resources.ITree): void;
    // (undocumented)
    createBlob(content: string, encoding: "utf-8" | "base64"): Promise<resources.ICreateBlobResponse>;
    // (undocumented)
    createCommit(commit: resources.ICreateCommitParams): Promise<resources.ICommit>;
    // (undocumented)
    createGitTree(params: resources.ICreateTreeParams): Promise<resources.ITree>;
    // (undocumented)
    createRef(branch: string, sha: string): Promise<resources.IRef>;
    // (undocumented)
    createSummary(summary: IWholeSummaryPayload): Promise<IWriteSummaryResponse>;
    // (undocumented)
    createTree(files: api.ITree): Promise<resources.ITree>;
    // (undocumented)
    deleteSummary(softDelete: boolean): Promise<void>;
    // (undocumented)
    getBlob(sha: string): Promise<resources.IBlob>;
    // (undocumented)
    getCommit(sha: string): Promise<resources.ICommit>;
    getCommits(shaOrRef: string, count: number): Promise<resources.ICommitDetails[]>;
    getContent(commit: string, path: string): Promise<resources.IBlob>;
    // (undocumented)
    getFullTree(sha: string): Promise<any>;
    // (undocumented)
    getHeader(id: string, sha: string): Promise<api.ISnapshotTree>;
    // (undocumented)
    getRawUrl(sha: string): string;
    // (undocumented)
    getRef(ref: string): Promise<resources.IRef>;
    // (undocumented)
    getSummary(sha: string): Promise<IWholeFlatSummary>;
    getTree(root: string, recursive?: boolean): Promise<resources.ITree>;
    // (undocumented)
    upsertRef(branch: string, commitSha: string): Promise<resources.IRef>;
    write(branch: string, inputTree: api.ITree, parents: string[], message: string): Promise<resources.ICommit>;
}

// @public
export class Historian implements IHistorian {
    constructor(endpoint: string, historianApi: boolean, disableCache: boolean, restWrapper?: RestWrapper);
    // (undocumented)
    createBlob(blob: resources.ICreateBlobParams): Promise<resources.ICreateBlobResponse>;
    // (undocumented)
    createCommit(commit: resources.ICreateCommitParams): Promise<resources.ICommit>;
    // (undocumented)
    createRef(params: resources.ICreateRefParams): Promise<resources.IRef>;
    // (undocumented)
    createSummary(summary: IWholeSummaryPayload): Promise<IWriteSummaryResponse>;
    // (undocumented)
    createTag(tag: resources.ICreateTagParams): Promise<resources.ITag>;
    // (undocumented)
    createTree(tree: resources.ICreateTreeParams): Promise<resources.ITree>;
    // (undocumented)
    deleteRef(ref: string): Promise<void>;
    // (undocumented)
    deleteSummary(softDelete: boolean): Promise<void>;
    // (undocumented)
    endpoint: string;
    // (undocumented)
    getBlob(sha: string): Promise<resources.IBlob>;
    // (undocumented)
    getCommit(sha: string): Promise<resources.ICommit>;
    // (undocumented)
    getCommits(sha: string, count: number): Promise<resources.ICommitDetails[]>;
    // (undocumented)
    getContent(path: string, ref: string): Promise<any>;
    // (undocumented)
    getFullTree(sha: string): Promise<any>;
    // (undocumented)
    getHeader(sha: string): Promise<any>;
    // (undocumented)
    getRef(ref: string): Promise<resources.IRef>;
    // (undocumented)
    getRefs(): Promise<resources.IRef[]>;
    // (undocumented)
    getSummary(sha: string): Promise<IWholeFlatSummary>;
    // (undocumented)
    getTag(tag: string): Promise<resources.ITag>;
    // (undocumented)
    getTree(sha: string, recursive: boolean): Promise<resources.ITree>;
    // (undocumented)
    updateRef(ref: string, params: resources.IPatchRefParams): Promise<resources.IRef>;
}

// @public (undocumented)
export interface IAlfredTenant {
    // (undocumented)
    id: string;
    // (undocumented)
    key: string;
}

// @public
export interface ICreateRefParamsExternal extends resources.ICreateRefParams {
    // Warning: (ae-forgotten-export) The symbol "IExternalWriterConfig" needs to be exported by the entry point index.d.ts
    //
    // (undocumented)
    config?: IExternalWriterConfig;
}

// @public (undocumented)
export interface ICredentials {
    // (undocumented)
    password: string;
    // (undocumented)
    user: string;
}

// @public (undocumented)
export interface IEmbeddedSummaryHandle extends ISummaryHandle {
    // (undocumented)
    embedded: boolean;
}

// @public
export interface IGetRefParamsExternal {
    // (undocumented)
    config?: IExternalWriterConfig;
}

// @public
export interface IGitCache {
    // (undocumented)
    blobs: resources.IBlob[];
    // (undocumented)
    commits: resources.ICommit[];
    // (undocumented)
    refs: {
        [key: string]: string;
    };
    // (undocumented)
    trees: resources.ITree[];
}

// @public (undocumented)
export interface IGitManager {
    // (undocumented)
    createBlob(content: string, encoding: string): Promise<resources.ICreateBlobResponse>;
    // (undocumented)
    createCommit(commit: resources.ICreateCommitParams): Promise<resources.ICommit>;
    // (undocumented)
    createGitTree(params: resources.ICreateTreeParams): Promise<resources.ITree>;
    // (undocumented)
    createRef(branch: string, sha: string): Promise<resources.IRef>;
    // (undocumented)
    createSummary(summary: IWholeSummaryPayload): Promise<IWriteSummaryResponse>;
    // (undocumented)
    createTree(files: api.ITree): Promise<resources.ITree>;
    // (undocumented)
    deleteSummary(softDelete: boolean): Promise<void>;
    // (undocumented)
    getBlob(sha: string): Promise<resources.IBlob>;
    // (undocumented)
    getCommit(sha: string): Promise<resources.ICommit>;
    // (undocumented)
    getCommits(sha: string, count: number): Promise<resources.ICommitDetails[]>;
    // (undocumented)
    getContent(commit: string, path: string): Promise<resources.IBlob>;
    // (undocumented)
    getFullTree(sha: string): Promise<any>;
    // (undocumented)
    getHeader(id: string, sha: string): Promise<api.ISnapshotTree>;
    // (undocumented)
    getRawUrl(sha: string): string;
    // (undocumented)
    getRef(ref: string): Promise<resources.IRef>;
    // (undocumented)
    getSummary(sha: string): Promise<IWholeFlatSummary>;
    // (undocumented)
    getTree(root: string, recursive: boolean): Promise<resources.ITree>;
    // (undocumented)
    upsertRef(branch: string, commitSha: string): Promise<resources.IRef>;
    // (undocumented)
    write(branch: string, inputTree: api.ITree, parents: string[], message: string): Promise<resources.ICommit>;
}

// @public
export interface IGitService {
    // (undocumented)
    createBlob(blob: resources.ICreateBlobParams): Promise<resources.ICreateBlobResponse>;
    // (undocumented)
    createCommit(commit: resources.ICreateCommitParams): Promise<resources.ICommit>;
    // (undocumented)
    createRef(params: resources.ICreateRefParams): Promise<resources.IRef>;
    // (undocumented)
    createSummary(summary: IWholeSummaryPayload): Promise<IWriteSummaryResponse>;
    // (undocumented)
    createTag(tag: resources.ICreateTagParams): Promise<resources.ITag>;
    // (undocumented)
    createTree(tree: resources.ICreateTreeParams): Promise<resources.ITree>;
    // (undocumented)
    deleteRef(ref: string): Promise<void>;
    // (undocumented)
    deleteSummary(softDelete: boolean): Promise<void>;
    // (undocumented)
    getBlob(sha: string): Promise<resources.IBlob>;
    // (undocumented)
    getCommit(sha: string): Promise<resources.ICommit>;
    // (undocumented)
    getCommits(sha: string, count: number): Promise<resources.ICommitDetails[]>;
    // (undocumented)
    getContent(path: string, ref: string): Promise<any>;
    // (undocumented)
    getRef(ref: string): Promise<resources.IRef>;
    // (undocumented)
    getRefs(): Promise<resources.IRef[]>;
    // (undocumented)
    getSummary(sha: string): Promise<IWholeFlatSummary>;
    // (undocumented)
    getTag(tag: string): Promise<resources.ITag>;
    // (undocumented)
    getTree(sha: string, recursive: boolean): Promise<resources.ITree>;
    // (undocumented)
    updateRef(ref: string, params: resources.IPatchRefParams): Promise<resources.IRef>;
}

// @public
export interface IHistorian extends IGitService {
    // (undocumented)
    endpoint: string;
    // (undocumented)
    getFullTree(sha: string): Promise<any>;
    getHeader(sha: string): Promise<resources.IHeader>;
}

// @public
export interface INormalizedWholeSummary {
    // (undocumented)
    blobs: Map<string, ArrayBuffer>;
    // (undocumented)
    sequenceNumber: number | undefined;
    // (undocumented)
    snapshotTree: ISnapshotTree;
}

// @public
export interface IPatchRefParamsExternal extends resources.IPatchRefParams {
    // (undocumented)
    config?: IExternalWriterConfig;
}

// @public (undocumented)
export interface ISummaryTree extends ISummaryTree_2 {
    // (undocumented)
    tree: {
        [path: string]: ExtendedSummaryObject;
    };
}

// @public
export interface ISummaryUploadManager {
    writeSummaryTree(summaryTree: api.ISummaryTree, parentHandle: string, summaryType: IWholeSummaryPayloadType, sequenceNumber?: number): Promise<string>;
}

// @public (undocumented)
export interface IWholeFlatSummary {
    // (undocumented)
    blobs?: IWholeFlatSummaryBlob[];
    // (undocumented)
    id: string;
    // (undocumented)
    trees: IWholeFlatSummaryTree[];
}

// @public (undocumented)
export interface IWholeFlatSummaryBlob {
    // (undocumented)
    content: string;
    // (undocumented)
    encoding: "base64" | "utf-8";
    // (undocumented)
    id: string;
    // (undocumented)
    size: number;
}

// @public (undocumented)
export interface IWholeFlatSummaryTree {
    // (undocumented)
    entries: IWholeFlatSummaryTreeEntry[];
    // (undocumented)
    id: string;
    // (undocumented)
    sequenceNumber: number;
}

// @public (undocumented)
export type IWholeFlatSummaryTreeEntry = IWholeFlatSummaryTreeEntryTree | IWholeFlatSummaryTreeEntryBlob;

// @public (undocumented)
export interface IWholeFlatSummaryTreeEntryBlob {
    // (undocumented)
    id: string;
    // (undocumented)
    path: string;
    // (undocumented)
    type: "blob";
}

// @public (undocumented)
export interface IWholeFlatSummaryTreeEntryTree {
    // (undocumented)
    path: string;
    // (undocumented)
    type: "tree";
    // (undocumented)
    unreferenced?: true;
}

// @public (undocumented)
export interface IWholeSummaryBlob {
    // (undocumented)
    content: string;
    // (undocumented)
    encoding: "base64" | "utf-8";
    // (undocumented)
    type: "blob";
}

// @public (undocumented)
export interface IWholeSummaryPayload {
    // (undocumented)
    entries: WholeSummaryTreeEntry[];
    // (undocumented)
    message: string;
    // (undocumented)
    sequenceNumber: number;
    // (undocumented)
    type: IWholeSummaryPayloadType;
}

// @public (undocumented)
export type IWholeSummaryPayloadType = "container" | "channel";

// @public (undocumented)
export interface IWholeSummaryTree {
    // (undocumented)
    entries?: WholeSummaryTreeEntry[];
    // (undocumented)
    type: "tree";
}

// @public (undocumented)
export interface IWholeSummaryTreeBaseEntry {
    // (undocumented)
    path: string;
    // (undocumented)
    type: "blob" | "tree" | "commit";
}

// @public (undocumented)
export interface IWholeSummaryTreeHandleEntry extends IWholeSummaryTreeBaseEntry {
    // (undocumented)
    id: string;
}

// @public (undocumented)
export interface IWholeSummaryTreeValueEntry extends IWholeSummaryTreeBaseEntry {
    // (undocumented)
    unreferenced?: true;
    // (undocumented)
    value: WholeSummaryTreeValue;
}

// @public (undocumented)
export interface IWriteSummaryResponse {
    // (undocumented)
    id: string;
}

// @public (undocumented)
export class NetworkError extends Error {
    constructor(
    code: number, message: string);
    readonly code: number;
}

// @public (undocumented)
export function promiseTimeout(mSec: number, promise: Promise<any>): Promise<any>;

// @public
export class RestLessClient {
    translate(request: AxiosRequestConfig): AxiosRequestConfig;
}

// @public (undocumented)
export enum RestLessFieldNames {
    // (undocumented)
    Body = "body",
    // (undocumented)
    Header = "header",
    // (undocumented)
    Method = "method"
}

// @public (undocumented)
export abstract class RestWrapper {
    constructor(baseurl?: string, defaultQueryString?: Record<string, unknown>, maxBodyLength?: number, maxContentLength?: number);
    // (undocumented)
    protected readonly baseurl?: string;
    // (undocumented)
    protected defaultQueryString: Record<string, unknown>;
    // (undocumented)
    delete<T>(url: string, queryString?: Record<string, unknown>, headers?: Record<string, unknown>): Promise<T>;
    // (undocumented)
    protected generateQueryString(queryStringValues: Record<string, unknown>): string;
    // (undocumented)
    get<T>(url: string, queryString?: Record<string, unknown>, headers?: Record<string, unknown>): Promise<T>;
    // (undocumented)
    protected readonly maxBodyLength: number;
    // (undocumented)
    protected readonly maxContentLength: number;
    // (undocumented)
    patch<T>(url: string, requestBody: any, queryString?: Record<string, unknown>, headers?: Record<string, unknown>): Promise<T>;
    // (undocumented)
    post<T>(url: string, requestBody: any, queryString?: Record<string, unknown>, headers?: Record<string, unknown>): Promise<T>;
    // (undocumented)
    protected abstract request<T>(options: AxiosRequestConfig, statusCode: number): Promise<T>;
}

// @public
export class SummaryTreeUploadManager implements ISummaryUploadManager {
    constructor(manager: IGitManager, blobsShaCache: Map<string, string>, getPreviousFullSnapshot: (parentHandle: string) => Promise<ISnapshotTreeEx | null | undefined>);
    // (undocumented)
    writeSummaryTree(summaryTree: ISummaryTree_2, parentHandle: string, summaryType: IWholeSummaryPayloadType, sequenceNumber?: number): Promise<string>;
    }

// @public
export function validateTokenClaims(token: string, documentId: string, tenantId: string): ITokenClaims;

// @public
export function validateTokenClaimsExpiration(claims: ITokenClaims, maxTokenLifetimeSec: number): number;

// @public (undocumented)
export type WholeSummaryTreeEntry = IWholeSummaryTreeValueEntry | IWholeSummaryTreeHandleEntry;

// @public (undocumented)
export type WholeSummaryTreeValue = IWholeSummaryTree | IWholeSummaryBlob;

// @public
export class WholeSummaryUploadManager implements ISummaryUploadManager {
    constructor(manager: IGitManager);
    // (undocumented)
    writeSummaryTree(summaryTree: ISummaryTree, parentHandle: string | undefined, summaryType: IWholeSummaryPayloadType, sequenceNumber?: number): Promise<string>;
    }


// (No @packageDocumentation comment for this package)

```