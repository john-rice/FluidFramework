## API Report File for "@fluidframework/task-manager"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { IChannelAttributes } from '@fluidframework/datastore-definitions';
import { IChannelFactory } from '@fluidframework/datastore-definitions';
import { IChannelStorageService } from '@fluidframework/datastore-definitions';
import { IFluidDataStoreRuntime } from '@fluidframework/datastore-definitions';
import { IFluidSerializer } from '@fluidframework/shared-object-base';
import { ISequencedDocumentMessage } from '@fluidframework/protocol-definitions';
import { ISharedObject } from '@fluidframework/shared-object-base';
import { ISharedObjectEvents } from '@fluidframework/shared-object-base';
import { ISummaryTreeWithStats } from '@fluidframework/runtime-definitions';
import { SharedObject } from '@fluidframework/shared-object-base';

// @public
export interface ITaskManager extends ISharedObject<ITaskManagerEvents> {
    abandon(taskId: string): void;
    assigned(taskId: string): boolean;
    canVolunteer(): boolean;
    complete(taskId: string): void;
    queued(taskId: string): boolean;
    subscribed(taskId: string): boolean;
    subscribeToTask(taskId: string): void;
    volunteerForTask(taskId: string): Promise<boolean>;
}

// @public
export interface ITaskManagerEvents extends ISharedObjectEvents {
    // @eventProperty
    (event: "assigned", listener: TaskEventListener): any;
    // @eventProperty
    (event: "completed", listener: TaskEventListener): any;
    // @eventProperty
    (event: "lost", listener: TaskEventListener): any;
}

// @public
export type TaskEventListener = (taskId: string) => void;

// @public @sealed
export class TaskManager extends SharedObject<ITaskManagerEvents> implements ITaskManager {
    constructor(id: string, runtime: IFluidDataStoreRuntime, attributes: IChannelAttributes);
    abandon(taskId: string): void;
    // (undocumented)
    applyStashedOp(): void;
    assigned(taskId: string): boolean;
    canVolunteer(): boolean;
    complete(taskId: string): void;
    static create(runtime: IFluidDataStoreRuntime, id?: string): TaskManager;
    static getFactory(): IChannelFactory;
    // @internal (undocumented)
    protected initializeLocalCore(): void;
    // @internal (undocumented)
    protected loadCore(storage: IChannelStorageService): Promise<void>;
    // @internal (undocumented)
    protected onConnect(): void;
    // @internal (undocumented)
    protected onDisconnect(): void;
    // @internal
    protected processCore(message: ISequencedDocumentMessage, local: boolean, localOpMetadata: unknown): void;
    queued(taskId: string): boolean;
    // @internal
    protected reSubmitCore(): void;
    subscribed(taskId: string): boolean;
    subscribeToTask(taskId: string): void;
    // @internal
    protected summarizeCore(serializer: IFluidSerializer): ISummaryTreeWithStats;
    volunteerForTask(taskId: string): Promise<boolean>;
}

```